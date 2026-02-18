---
type: anomaly
id: ANOM-003
title: Recording playback delay exceeds 2s on low-memory devices
status: draft
category: performance
severity: minor
disposition: deferred
affected_version: '1.3.0'
author: rune@ords.io
reviewers:
  - engineering
approvers:
  - engineering
---

# ANOM-003: Recording playback delay exceeds 2s on low-memory devices

## Description

On devices with less than 3GB RAM, loading a previously recorded ECG session for playback takes more than 2 seconds, exceeding the UI responsiveness target defined in [SRS-004](../../software/requirements/SRS-004.md). The delay occurs during decompression of the stored signal data.

## Affected Components

- Local storage module
- Signal decompression routine

## Impact Assessment

- **Patient safety**: None — this is a playback-only issue; real-time monitoring and detection are unaffected.
- **Usability**: Minor — users experience a brief loading spinner. No data loss or corruption.
- **Clinical workflow**: Negligible — does not affect clinical decision-making.

## Disposition Rationale

Deferred to next release cycle. The issue affects <5% of active devices and does not impact safety or clinical accuracy. A loading indicator is displayed during the delay, meeting minimum usability requirements.

## Planned Resolution

Implement streaming decompression to reduce peak memory usage and improve perceived load time. Target: <500ms on all supported devices.
