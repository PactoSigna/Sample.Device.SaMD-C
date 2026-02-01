---
id: HAZ-US-001
title: Clinician Misreads Confidence Score
status: approved
author: engineering@pactosigna.com
reviewers:
  - quality
  - clinical
approvers:
  - quality-lead
analyzes: UN-002
---

# Hazard: Clinician Misreads Confidence Score

## Description

The clinician misinterprets the detection confidence score due to unclear visual presentation, leading to incorrect clinical decisions.

## Usability FMEA Analysis

**Use Error:** Clinician interprets low confidence as "unreliable/ignore" rather than "needs follow-up"

**Task Context:**

- Clinician reviewing multiple patient records
- Time pressure during busy clinic hours
- Variable experience with device interface

**Detection Method:**

- Usability testing with representative clinicians
- Post-market surveillance of user feedback
- Analysis of clinical decision patterns

## Hazardous Situations

This hazard can lead to:

- [HS-002](../situations/HS-002.md) - Clinician dismisses valid AFib detection
