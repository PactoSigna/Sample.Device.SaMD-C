---
documentId: TEST-001
title: AFib Sensitivity Validation Test
docType: test-case
status: approved
---

# TEST-001: AFib Sensitivity Validation Test

## Test Objective

Verify that the CardioSense AFib detection algorithm achieves ≥ 95% sensitivity as required by REQ-001.

## Test Configuration

### Test Environment
- Software version: [Release candidate version]
- Hardware: Standard deployment configuration
- Test dataset: CardioSense Validation Dataset v2.0

### Dataset Requirements
- Minimum 500 confirmed AFib episodes
- Ground truth established by consensus of 3 board-certified cardiologists
- Demographics representative of intended use population
- Signal quality distribution matching real-world usage

## Preconditions

1. Algorithm has passed unit tests and integration tests
2. Validation dataset is locked and version-controlled
3. Test environment matches production configuration
4. Independent tester (not involved in algorithm development) conducts test

## Test Procedure

### Step 1: Dataset Preparation
1. Load validation dataset (n ≥ 500 AFib episodes)
2. Verify dataset integrity (checksums)
3. Confirm ground truth labels are blinded from tester

### Step 2: Algorithm Execution
1. Process each ECG recording through the detection pipeline
2. Record algorithm output (Detected/Not Detected) for each recording
3. Log processing time and any errors

### Step 3: Result Comparison
1. Compare algorithm outputs to ground truth labels
2. Calculate:
   - True Positives (TP): AFib correctly detected
   - False Negatives (FN): AFib missed by algorithm
   - Sensitivity = TP / (TP + FN)

### Step 4: Statistical Analysis
1. Calculate point estimate of sensitivity
2. Calculate 95% confidence interval (Wilson score method)
3. Perform subgroup analysis by:
   - Age group (< 65, ≥ 65)
   - Signal quality (Good, Acceptable, Poor)
   - AFib episode duration

## Expected Results

| Metric | Requirement | Acceptance Criterion |
|--------|-------------|---------------------|
| Sensitivity (overall) | ≥ 95% | Lower bound of 95% CI ≥ 93% |
| Sensitivity (age < 65) | ≥ 93% | Point estimate |
| Sensitivity (age ≥ 65) | ≥ 93% | Point estimate |
| Sensitivity (good quality) | ≥ 97% | Point estimate |
| Sensitivity (acceptable quality) | ≥ 94% | Point estimate |

## Pass/Fail Criteria

**PASS**: Overall sensitivity ≥ 95% with lower 95% CI bound ≥ 93%

**FAIL**: Overall sensitivity < 95% OR lower 95% CI bound < 93%

## Test Records

| Field | Value |
|-------|-------|
| Test Date | [To be completed] |
| Tester | [To be completed] |
| Software Version | [To be completed] |
| Dataset Version | [To be completed] |
| Result | [PASS/FAIL] |

## Observations

[To be completed during test execution]

## Links

- verifies: REQ-001
