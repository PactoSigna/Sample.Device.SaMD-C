---
documentId: ARCH-001
title: Signal Processing Pipeline Architecture
docType: architecture
status: approved
---

# ARCH-001: Signal Processing Pipeline Architecture

## Overview

This document describes the architecture of the CardioSense ECG signal processing pipeline, which transforms raw ECG data into AFib detection results.

## System Context

```
┌─────────────────┐     ┌──────────────────────────────────────────────┐     ┌─────────────────┐
│   ECG Source    │────▶│         Signal Processing Pipeline           │────▶│   User Alert    │
│  (Wearable/     │     │                                              │     │   Interface     │
│   Monitor)      │     └──────────────────────────────────────────────┘     └─────────────────┘
└─────────────────┘
```

## Pipeline Components

### 1. Signal Acquisition Module

**Purpose**: Receive and buffer incoming ECG data streams

**Inputs**:
- Raw ECG signal (sampling rate: 250-500 Hz)
- Device metadata (gain, lead configuration)

**Outputs**:
- Buffered signal segments (30-second windows)
- Signal quality indicators

**Key Design Decisions**:
- 30-second analysis windows balance detection latency with algorithm accuracy
- Overlapping windows (50%) ensure no AFib episodes span window boundaries undetected

### 2. Preprocessing Module

**Purpose**: Clean and normalize ECG signals for analysis

**Processing Steps**:
1. **Baseline Wander Removal**: High-pass filter (0.5 Hz cutoff)
2. **Powerline Interference**: Notch filter (50/60 Hz)
3. **High-frequency Noise**: Low-pass filter (40 Hz cutoff)
4. **Amplitude Normalization**: Z-score normalization per segment

**Signal Quality Assessment**:
- SNR calculation
- Artifact detection (motion, electrode contact)
- Quality classification: Good / Acceptable / Poor / Unusable

### 3. Feature Extraction Module

**Purpose**: Extract clinically relevant features for AFib detection

**RR Interval Analysis**:
- R-peak detection using Pan-Tompkins algorithm
- RR interval time series generation
- Heart rate variability metrics:
  - RMSSD (root mean square of successive differences)
  - pNN50 (percentage of intervals differing by >50ms)
  - Sample entropy

**P-wave Analysis**:
- P-wave presence/absence detection
- P-wave morphology consistency scoring

**Rhythm Regularity**:
- Coefficient of variation of RR intervals
- Poincaré plot metrics (SD1, SD2)

### 4. Classification Module

**Purpose**: Determine AFib presence from extracted features

**Algorithm**: Ensemble classifier combining:
- Gradient Boosted Trees (primary)
- Deep Neural Network (secondary)
- Rule-based clinical criteria (validation)

**Output**:
- Binary classification: AFib Detected / Not Detected
- Confidence score (0-100%)
- Supporting evidence summary

**Thresholds**:
- Detection threshold: Confidence ≥ 70%
- High-confidence threshold: Confidence ≥ 90%

### 5. Result Aggregation Module

**Purpose**: Combine window-level results into episode-level detections

**Logic**:
- AFib episode: ≥ 2 consecutive windows with detection
- Episode duration: Start of first window to end of last window
- Merge episodes separated by < 60 seconds

## Data Flow Diagram

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│   Signal     │    │   Pre-       │    │   Feature    │    │   Classifi-  │    │   Result     │
│   Acquisition│───▶│   processing │───▶│   Extraction │───▶│   cation     │───▶│   Aggregation│
│              │    │              │    │              │    │              │    │              │
│ 30s windows  │    │ Filtered     │    │ HRV metrics  │    │ AFib/Normal  │    │ Episode      │
│ @ 250 Hz     │    │ normalized   │    │ P-wave feat. │    │ + confidence │    │ detections   │
└──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘
```

## Performance Requirements

| Metric | Requirement | Rationale |
|--------|-------------|-----------|
| Processing latency | < 5 seconds per window | Support 30-second alert requirement |
| Memory usage | < 256 MB | Mobile device compatibility |
| CPU usage | < 50% single core | Background operation |

## Security Considerations

- All ECG data encrypted at rest (AES-256)
- TLS 1.3 for data in transit
- No PII stored with signal data
- Audit logging of all data access

## Links

- implements: REQ-001
- implements: REQ-002
