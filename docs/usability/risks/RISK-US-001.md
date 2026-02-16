---
id: RISK-US-001
title: Misinterpretation of Detection Results
status: approved
author: rune@ords.io
reviewers:
  - quality
approvers:
  - quality
---

# Risk Analysis: Misinterpretation of Detection Results

## Risk Path

**Analyzes:** [TA-001](../task-analyses/TA-001.md)
**Leads to:** [HS-002](../../risk/situations/HS-002.md)
**Results in:** [HARM-001](../../risk/harms/HARM-001.md)

## Inherent Risk Assessment

| Factor            | Rating        | Justification                                |
| ----------------- | ------------- | -------------------------------------------- |
| Severity          | 4 (Critical)  | Dismissed detection could lead to stroke     |
| Probability       | 2 (Remote)    | Clinicians generally trained, but errors occur |
| **Inherent Risk** | **8 - ALARP** | Reduce as low as reasonably practicable      |

## Risk Controls

### [PRS-003](../../product-requirements/PRS-003.md) - Clear Detection Confidence Indicators

**Reduces:** sequence_probability

Require clear visual indicators (color coding, numerical percentage) that clinicians can interpret at a glance.

**Derives to:** [SRS-003](../../software-requirements/SRS-003.md)
**Verification:** [TC-004](../../test/TC-004.md)

## Residual Risk Assessment

| Factor            | Rating             | Justification                                    |
| ----------------- | ------------------ | ------------------------------------------------ |
| Severity          | 4 (Critical)       | Unchanged                                        |
| Probability       | 1 (Rare)           | Clear UI reduces misinterpretation significantly |
| **Residual Risk** | **4 - Acceptable** | Within tolerance                                 |

## Risk-Benefit Analysis

Not required - residual risk is acceptable.
