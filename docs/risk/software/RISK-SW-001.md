---
id: RISK-SW-001
title: False Negative Detection Risk
status: approved
author: engineering@pactosigna.com
reviewers:
  - quality
approvers:
  - quality-lead
  - regulatory
---

# Risk Analysis: False Negative Detection Risk

## Risk Path

**Analyzes:** [HAZ-SW-001](HAZ-SW-001.md)
**Leads to:** [HS-001](../situations/HS-001.md)
**Results in:** [HARM-001](../harms/HARM-001.md)

## Inherent Risk Assessment

| Factor            | Rating                | Justification                                       |
| ----------------- | --------------------- | --------------------------------------------------- |
| Severity          | 4 (Critical)          | Stroke can cause death or permanent disability      |
| Probability       | 3 (Occasional)        | Algorithm limitations without controls, ~5% FN rate |
| **Inherent Risk** | **12 - Unacceptable** | Requires mitigation                                 |

## Risk Controls

### [SRS-002](../../software-requirements/SRS-002.md) - Validated ML Algorithm

**Reduces:** sequence_probability

Require algorithm trained on >=10,000 recordings with >=95% sensitivity validation.

**Verification:** [TC-001](../../test/TC-001.md)

### [SRS-004](../../software-requirements/SRS-004.md) - Signal Quality Threshold

**Reduces:** sequence_probability

Suppress results when signal quality is poor, preventing unreliable negative results.

**Verification:** [TC-003](../../test/TC-003.md)

## Residual Risk Assessment

| Factor            | Rating             | Justification                          |
| ----------------- | ------------------ | -------------------------------------- |
| Severity          | 4 (Critical)       | Unchanged - harm severity if it occurs |
| Probability       | 1 (Rare)           | Controls reduce FN rate to <1%         |
| **Residual Risk** | **4 - Acceptable** | Within tolerance                       |

## Risk-Benefit Analysis

Not required - residual risk is acceptable.
