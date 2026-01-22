---
documentId: TEST-002
title: AFib Specificity Validation Test
docType: test-case
status: approved
---

# TEST-002: AFib Specificity Validation Test

## Test Objective

Verify that the CardioSense AFib detection algorithm achieves ≥ 90% specificity as required by REQ-002.

## Test Configuration

### Test Environment
- Software version: [Release candidate version]
- Hardware: Standard deployment configuration
- Test dataset: CardioSense Validation Dataset v2.0

### Dataset Requirements
- Minimum 500 non-AFib recordings
- Includes common AFib mimics:
  - Normal sinus rhythm
  - Sinus arrhythmia
  - Premature atrial contractions (PACs)
  - Premature ventricular contractions (PVCs)
  - Motion artifact
- Ground truth established by consensus of 3 board-certified cardiologists
- Demographics representative of intended use population

## Preconditions

1. Algorithm has passed unit tests and integration tests
2. Validation dataset is locked and version-controlled
3. Test environment matches production configuration
4. Independent tester (not involved in algorithm development) conducts test

## Test Procedure

### Step 1: Dataset Preparation
1. Load validation dataset (n ≥ 500 non-AFib recordings)
2. Verify dataset integrity (checksums)
3. Confirm ground truth labels are blinded from tester

### Step 2: Algorithm Execution
1. Process each ECG recording through the detection pipeline
2. Record algorithm output (Detected/Not Detected) for each recording
3. Log processing time and any errors

### Step 3: Result Comparison
1. Compare algorithm outputs to ground truth labels
2. Calculate:
   - True Negatives (TN): Non-AFib correctly identified
   - False Positives (FP): Non-AFib incorrectly flagged as AFib
   - Specificity = TN / (TN + FP)

### Step 4: Statistical Analysis
1. Calculate point estimate of specificity
2. Calculate 95% confidence interval (Wilson score method)
3. Perform subgroup analysis by:
   - Rhythm type (normal sinus, PACs, PVCs, artifact)
   - Signal quality (Good, Acceptable, Poor)

## Expected Results

| Metric | Requirement | Acceptance Criterion |
|--------|-------------|---------------------|
| Specificity (overall) | ≥ 90% | Lower bound of 95% CI ≥ 88% |
| Specificity (normal sinus) | ≥ 95% | Point estimate |
| Specificity (PACs) | ≥ 85% | Point estimate |
| Specificity (artifact) | ≥ 80% | Point estimate |

## Pass/Fail Criteria

**PASS**: Overall specificity ≥ 90% with lower 95% CI bound ≥ 88%

**FAIL**: Overall specificity < 90% OR lower 95% CI bound < 88%

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

- verifies: REQ-002
