# Sample.Device.SaMD-C

**CardioSense - Cardiac Arrhythmia Detection SaMD (Class C)**

This repository contains a complete Technical File / Design History File (DHF) for a hypothetical Software as a Medical Device (SaMD) that analyzes ECG data to detect atrial fibrillation.

## Purpose

This is a **gold-standard sample repository** designed for use with [PactoSigna](https://pactosigna.com). Fork this repository to your organization and use it as a starting point for your own medical device documentation.

## How to Use

### 1. Fork This Repository

Click the "Fork" button above to copy this repository to your GitHub organization.

### 2. Connect to PactoSigna

1. Log in to PactoSigna
2. Navigate to Repositories
3. Click "Connect Repository"
4. Select your forked repository

### 3. Customize with AI

Use your preferred AI assistant to adapt this documentation for your specific device. Example prompts:

**Adapt the device type:**
> "Act as a Regulatory Affairs Specialist. Update all User Needs and Requirements in this repository to describe a continuous glucose monitoring (CGM) SaMD instead of cardiac arrhythmia detection. Maintain the same document structure and traceability links."

**Expand risk analysis:**
> "Act as a Risk Management Engineer. Review SR-001 and identify 3 additional software failure modes for the detection algorithm. Create new SR-002, SR-003, SR-004 documents following the same format."

**Generate test cases:**
> "Act as a V&V Engineer. Based on REQ-001 through REQ-004, generate detailed test cases with preconditions, steps, and expected results. Ensure full requirements coverage."

## Repository Structure

```
docs/
├── plans/                    # Development and Risk Management Plans
│   ├── DEV-PLAN-001.md
│   └── RISK-PLAN-001.md
├── user-needs/               # User Needs
│   ├── UN-001.md            # Detect AFib accurately
│   ├── UN-002.md            # Alert user promptly
│   └── UN-003.md            # Work with common ECG sources
├── requirements/             # Software Requirements
│   ├── REQ-001.md           # AFib detection sensitivity ≥95%
│   ├── REQ-002.md           # AFib detection specificity ≥90%
│   ├── REQ-003.md           # Algorithm validation control
│   └── REQ-004.md           # Alert latency <30 seconds
├── architecture/             # Architecture Documents
│   └── ARCH-001.md          # Signal processing pipeline
├── risks/                    # Risk Analysis
│   ├── software/
│   │   ├── SR-001.md        # False negative detection
│   │   └── SR-002.md        # Algorithm drift
│   └── security/
│       └── SEC-001.md       # Data integrity threat
└── tests/                    # Test Cases
    ├── TEST-001.md          # AFib sensitivity validation
    ├── TEST-002.md          # Specificity validation
    └── TEST-003.md          # Alert latency test
```

## Traceability

This repository demonstrates complete traceability chains:

```
UN-001 (Detect AFib accurately)
   ├── derives → REQ-001 (Sensitivity ≥95%)
   │                ├── implements → ARCH-001 (Signal processing pipeline)
   │                └── verified_by → TEST-001 (Sensitivity validation)
   │
   └── derives → REQ-002 (Specificity ≥90%)
                    └── verified_by → TEST-002 (Specificity validation)

SR-001 (False negative detection risk)
   └── mitigates → REQ-003 (Algorithm validation control)
```

## Document Status

| Document | Status | Description |
|----------|--------|-------------|
| UN-001, REQ-001, REQ-002, REQ-003, ARCH-001, SR-001, TEST-001, TEST-002 | Complete | Fully written examples |
| All others | Skeleton | Template structure for you to complete |

## License

This sample repository is provided under the MIT License for educational and commercial use.

---

*Built for [PactoSigna](https://pactosigna.com) - AI-native Quality Management for Medical Device Software*
