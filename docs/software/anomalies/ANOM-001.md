---
type: anomaly
id: ANOM-001
title: AFib detection false positive during sinus arrhythmia
status: approved
category: bug
severity: major
disposition: resolved
affected_version: '1.1.0'
author: rune@ords.io
reviewers:
  - engineering
  - quality
approvers:
  - engineering
---

# ANOM-001: AFib detection false positive during sinus arrhythmia

## Description

The AFib detection algorithm incorrectly classifies sinus arrhythmia (a benign, physiological variation in heart rate) as atrial fibrillation in approximately 3% of recordings from patients aged 18–25. This leads to false positive alerts that may cause unnecessary clinical follow-up.

## Affected Components

- TensorFlow inference model (SOUP-01)
- Signal processing pipeline (SRS-001)

## Root Cause

The R-R interval variability threshold used for AFib classification was calibrated on a dataset that under-represented younger populations with high vagal tone, where sinus arrhythmia produces R-R variability patterns that overlap with mild AFib.

## Impact Assessment

- **Patient safety**: Low — false positive only (no missed diagnoses). May cause patient anxiety and unnecessary follow-up appointments.
- **Clinical workflow**: Moderate — estimated 3% increase in false positive alerts for the affected age group.
- **Regulatory**: Requires disclosure in release notes per IEC 62304 §9.8.

## Resolution

Implemented a secondary classifier that distinguishes respiratory sinus arrhythmia from AFib by correlating R-R variability with respiratory rate estimation. Validated against expanded dataset including 500 additional recordings from patients aged 18–30.

See [TP-001](../../test/protocols/TP-001.md) for updated validation protocol.

## Verification

- Retrained model reduces false positive rate to <0.5% in the affected demographic
- Regression testing confirms no degradation in sensitivity for true AFib cases
- Test report: [TR-001](../../test/reports/TR-001.md)
