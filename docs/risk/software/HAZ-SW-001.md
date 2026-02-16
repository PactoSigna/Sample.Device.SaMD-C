---
id: HAZ-SW-001
title: Algorithm Fails to Detect Irregular Rhythm
status: approved
author: rune@ords.io
reviewers:
  - quality
approvers:
  - engineering
  - quality
analyzes: SRS-002
---

# Hazard: Algorithm Fails to Detect Irregular Rhythm

## Description

The R-R interval analysis algorithm fails to correctly identify atrial fibrillation patterns, resulting in a false negative detection.

## sFMEA Analysis

**Failure Mode:** AFib detection algorithm returns negative result when AFib is present

**Cause:**

- Atypical R-R variability pattern not in training data
- Edge case in neural network classification
- Floating point precision issues in feature calculation

**Detection Method:**

- Automated unit tests with boundary value analysis
- Validation against expert-labeled dataset
- Real-time monitoring of detection distribution
- QA review during each release

## Hazardous Situations

This hazard can lead to:

- [HS-001](../situations/HS-001.md) - Patient with undetected AFib does not seek treatment
