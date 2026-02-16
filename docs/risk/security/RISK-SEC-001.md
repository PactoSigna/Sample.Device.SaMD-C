---
id: RISK-SEC-001
title: Unauthorized Access to Patient Detection Data
status: approved
author: rune@ords.io
reviewers:
  - quality
  - security
approvers:
  - quality
---

# Risk Analysis: Unauthorized Access to Patient Detection Data

## Risk Path

**Analyzes:** [HAZ-SEC-001](HAZ-SEC-001.md)
**Leads to:** [HS-001](../situations/HS-001.md)
**Results in:** [HARM-002](../harms/HARM-002.md)

## Inherent Risk Assessment

| Factor            | Rating                | Justification                                         |
| ----------------- | --------------------- | ----------------------------------------------------- |
| Severity          | 3 (Serious)           | Breach of patient health data confidentiality         |
| Probability       | 2 (Remote)            | Requires exploit of authentication or API boundary    |
| **Inherent Risk** | **6 - ALARP**         | Reduce as low as reasonably practicable               |

## Risk Controls

### [SRS-005](../../software-requirements/SRS-005.md) - Authentication and Access Control

**Reduces:** sequence_probability

Require authenticated sessions with role-based access control for all patient data endpoints.

**Verification:** [TC-002](../../test/TC-002.md)

### [SRS-006](../../software-requirements/SRS-006.md) - Data Encryption at Rest and in Transit

**Reduces:** sequence_probability

All patient data encrypted using AES-256 at rest and TLS 1.2+ in transit.

**Verification:** [TC-002](../../test/TC-002.md)

## Residual Risk Assessment

| Factor            | Rating             | Justification                                  |
| ----------------- | ------------------ | ---------------------------------------------- |
| Severity          | 3 (Serious)        | Unchanged - harm severity if it occurs         |
| Probability       | 1 (Rare)           | Controls reduce attack surface significantly   |
| **Residual Risk** | **3 - Acceptable** | Within tolerance                               |

## Risk-Benefit Analysis

Not required - residual risk is acceptable.
