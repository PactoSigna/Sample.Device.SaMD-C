---
type: soup_register
id: SOUP-001
title: SOUP Register
status: approved
author: rune@ords.io
reviewers:
  - engineering
approvers:
  - quality
---

# SOUP Register — CardioSense

## Purpose

This register documents all Software of Unknown Provenance (SOUP) used in CardioSense per IEC 62304:2015 clause 8.1. Each SOUP item is evaluated for its risk contribution and verified through integration testing.

## SOUP Items

| ID | Component | Version | Purpose | Safety Risk Class | Verification |
|----|-----------|---------|---------|-------------------|-------------|
| SOUP-01 | TensorFlow | 2.15.0 | ML model training and inference for AFib detection | Class C — directly processes clinical data | Algorithm validation (TP-001) |
| SOUP-02 | React Native | 0.73.4 | Mobile application framework | Class B — displays clinical results | UI integration tests |
| SOUP-03 | Firebase Auth | 10.8.0 | User authentication and session management | Class B — access control | Auth integration tests |
| SOUP-04 | Firebase Firestore | 10.8.0 | Cloud database for patient records | Class C — stores clinical data | Data integrity tests |
| SOUP-05 | NumPy | 1.26.3 | Numerical computation for signal processing | Class C — part of detection pipeline | Algorithm validation (TP-001) |
| SOUP-06 | SciPy | 1.12.0 | Signal filtering (bandpass, notch filters) | Class C — part of detection pipeline | Signal processing tests (TP-002) |
| SOUP-07 | Express.js | 4.18.2 | API server framework | Class A — infrastructure only | API integration tests |
| SOUP-08 | jsonwebtoken | 9.0.2 | JWT token generation and validation | Class B — authentication | Security tests (TR-PEN-001) |

## Evaluation Criteria

SOUP risk classification follows IEC 62304 clause 8.1.2:
- **Class C**: SOUP directly contributes to clinical decision-making or stores clinical data
- **Class B**: SOUP handles access control or displays clinical information
- **Class A**: SOUP provides non-clinical infrastructure

## Monitoring

All SOUP items are tracked in [SBOM-001](../../cybersecurity/sbom/SBOM-001.md) for vulnerability monitoring. Version updates require regression testing before deployment.
