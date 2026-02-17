# Sample.Device.SaMD-C

**CardioSense - Cardiac Arrhythmia Detection SaMD (Class C)**

This repository contains a complete Technical File / Design History File (DHF) for a hypothetical Software as a Medical Device (SaMD) that analyzes ECG data to detect atrial fibrillation. It is structured as a sample for [PactoSigna](https://pactosigna.com), the AI-native Quality Management System for medical device software.

## Purpose

This is a **gold-standard sample repository** designed for use with [PactoSigna](https://pactosigna.com). Fork this repository to your organization and use it as a starting point for your own medical device documentation.

The documentation set covers:

- **IEC 62304** software development lifecycle (User Needs through Verification)
- **ISO 14971** risk management (Risk Management Plan, Hazard Analysis, Hazardous Situations, Harms)
- **IEC 62366** usability engineering (Use Specifications, Task Analyses, Evaluations)
- **IEC 81001-5-1** cybersecurity (Cybersecurity Plan, SBOM, Security Risk Assessment, Penetration Testing)
- **MDR / FDA** clinical evaluation (Clinical Evaluation Plan and Report)
- **MDR Art. 84** post-market surveillance
- **MDR Annex I** labeling (Instructions for Use)

## Device Configuration

The `pactosigna.yml` file at the repository root declares the device metadata:

```yaml
device:
  name: CardioSense
  safety_class: C
  classification:
    eu: Class IIa
    us: Class II
```

This is parsed by PactoSigna during document sync and drives Class C validation gates during release.

## Repository Structure

```
pactosigna.yml                          # Device configuration
docs/
├── user-needs/                         # User Needs (IEC 62366 / Design Input)
│   ├── UN-001.md                       # Accurate Atrial Fibrillation Detection
│   └── UN-002.md                       # Timely User Alert
├── product-requirements/               # Product Requirements Specification
│   ├── PRS-001.md                      # AFib Detection Sensitivity >= 95%
│   ├── PRS-002.md                      # Alert Latency < 30s
│   ├── PRS-003.md                      # Clear Detection Confidence Indicators
│   └── PRS-004.md                      # Algorithm Validation Control
├── software-requirements/              # Software Requirements Specification
│   ├── SRS-001.md                      # ECG Signal Processing Pipeline
│   ├── SRS-002.md                      # Real-time Alert Engine
│   ├── SRS-003.md                      # Confidence Score Display
│   ├── SRS-004.md                      # Algorithm Validation Framework
│   ├── SRS-005.md                      # API Authentication & Authorization
│   └── SRS-006.md                      # Data Encryption at Rest and in Transit
├── architecture/                       # High-Level Design (IEC 62304)
│   └── HLD-001.md                      # Signal Processing Pipeline Architecture
├── design/                             # Software Detailed Design
│   └── SDD-001.md                      # Detailed Design Description
├── test/                               # Verification & Validation
│   ├── protocols/                      # Test Protocols
│   │   ├── TP-001.md                   # AFib Sensitivity Validation
│   │   ├── TP-002.md                   # Processing Performance Benchmark
│   │   ├── TP-003.md                   # Signal Quality Gating
│   │   └── TP-004.md                   # Confidence Display Verification
│   ├── reports/                        # Test Reports
│   │   ├── TR-001.md                   # AF Detection Sensitivity Report
│   │   ├── TR-002.md                   # Processing Performance Report
│   │   ├── TR-003.md                   # Signal Quality Gating Report
│   │   ├── TR-004.md                   # Confidence Display Report
│   │   └── TR-PEN-001.md              # Penetration Test Report
│   └── pentest-report.pdf              # Source PDF for TR-PEN-001
├── risk/                               # Risk Management (ISO 14971)
│   ├── plans/
│   │   └── RMP-001.md                  # Risk Management Plan
│   ├── situations/                     # Hazardous Situations
│   │   ├── HS-001.md                   # Patient with Undetected AFib
│   │   ├── HS-002.md                   # Clinician Dismisses Valid Detection
│   │   └── HS-003.md                   # Unauthorized Access to Patient Records
│   └── harms/                          # Patient Harms
│       ├── HARM-001.md                 # Stroke from Untreated AFib
│       ├── HARM-002.md                 # Delayed Treatment
│       └── HARM-003.md                 # Patient Data Breach
├── software/                           # Software Lifecycle (IEC 62304)
│   ├── plans/
│   │   └── DEV-PLAN-001.md             # Software Development Plan
│   ├── risks/                          # Software Failure Risks
│   │   ├── RISK-SW-001.md              # False Negative Detection Risk
│   │   └── HAZ-SW-001.md               # Algorithm Fails to Detect AFib
│   └── soup/
│       └── SOUP-001.md                 # SOUP Register
├── cybersecurity/                      # Cybersecurity (IEC 81001-5-1)
│   ├── plans/
│   │   └── CSPLAN-001.md               # Cybersecurity Plan
│   ├── risks/                          # Cybersecurity Risks
│   │   ├── RISK-SEC-001.md             # Data Breach Risk Assessment
│   │   └── HAZ-SEC-001.md              # API Exploit Hazard
│   └── sbom/
│       └── SBOM-001.md                 # Software Bill of Materials
├── clinical/                           # Clinical Evaluation (MDR / FDA)
│   ├── CEP-001.md                      # Clinical Evaluation Plan
│   └── CER-001.md                      # Clinical Evaluation Report
├── post-market/                        # Post-Market Surveillance (MDR Art. 84)
│   └── PMS-001.md                      # Post-Market Surveillance Plan
├── labeling/                           # Labeling (MDR Annex I)
│   └── LBL-001.md                      # Instructions for Use
└── usability/                          # Usability Engineering (IEC 62366)
    ├── UEP-001.md                      # Usability Engineering Plan
    ├── use-specifications/             # User Profiles
    │   ├── US-001.md                   # Patient Profile
    │   └── US-002.md                   # Clinician Profile
    ├── task-analyses/                  # Critical Task Analyses
    │   ├── TA-001.md                   # Review Detection Results
    │   ├── TA-002.md                   # Record ECG Data
    │   └── TA-003.md                   # Drill into Raw ECG Data
    ├── evaluations/                    # Formative & Summative Evaluations
    │   ├── FE-001.md                   # Confidence Score Display Evaluation
    │   └── SE-001.md                   # Summative Usability Evaluation
    └── risks/                          # Use-related Risks
        └── RISK-US-001.md              # Misinterpretation of Detection Results
```

## Traceability

This repository demonstrates complete traceability chains from User Needs through Verification:

### Requirements Chain

```
UN-001 (Accurate AFib Detection)
   ├── derives --> PRS-001 (Sensitivity >= 95%)
   │                ├── derives --> SRS-001 (Signal Processing Pipeline)
   │                │                └── implements --> HLD-001 (Pipeline Architecture)
   │                └── verified_by --> TP-001 (Sensitivity Validation)
   │
   └── derives --> PRS-003 (Clear Confidence Indicators)
                    ├── derives --> SRS-003 (Confidence Score Display)
                    └── verified_by --> TP-004 (Confidence Score Test)

UN-002 (Timely User Alert)
   └── derives --> PRS-002 (Alert Latency < 30s)
                    ├── derives --> SRS-002 (Real-time Alert Engine)
                    └── verified_by --> TP-003 (Alert Latency Test)
```

### Risk Chain (ISO 14971)

The risk management file follows the ISO 14971 chain: **Hazard --> Hazardous Situation --> Harm**.

```
Software Risk Chain:
HAZ-SW-001 (Algorithm Fails to Detect AFib)
   └── leads_to --> HS-001 (Patient with Undetected AFib)
                       └── results_in --> HARM-001 (Stroke from Untreated AFib)
   └── mitigated_by --> PRS-004 (Algorithm Validation Control)

Security Risk Chain:
HAZ-SEC-001 (API Exploit)
   └── leads_to --> HS-003 (Unauthorized Access to Patient Records)
                       └── results_in --> HARM-003 (Patient Data Breach)
   └── mitigated_by --> SRS-005 (API Authentication & Authorization)

Usability Risk Chain:
HS-002 (Clinician Dismisses Valid Detection)
   └── results_in --> HARM-002 (Delayed Treatment)
   └── mitigated_by --> PRS-003 (Clear Confidence Indicators)
```

## Usability Engineering (IEC 62366)

The `docs/usability/` folder contains a complete usability engineering file per IEC 62366-1:

| Document | Purpose |
|----------|---------|
| UEP-001 | Usability Engineering Plan - scope, methods, acceptance criteria |
| US-001, US-002 | Use Specifications - Patient and Clinician user profiles |
| TA-001 through TA-003 | Task Analyses - critical user tasks and failure modes |
| FE-001 | Formative Evaluation - confidence score display usability test |
| SE-001 | Summative Evaluation - final usability validation (15 participants) |
| RISK-US-001 | Use-related Risk - misinterpretation of detection results |

## Class C Validation Gates

When publishing a release, PactoSigna enforces these validation gates for Class C devices:

### Required Plans (must be approved)
- RMP-001 — Risk Management Plan
- DEV-PLAN-001 — Software Development Plan
- CSPLAN-001 — Cybersecurity Plan
- UEP-001 — Usability Engineering Plan
- CEP-001 — Clinical Evaluation Plan
- PMS-001 — Post-Market Surveillance Plan

### Required Artifacts (must exist)
- SOUP-001 — SOUP Register
- SBOM-001 — Software Bill of Materials
- SE-001 — Summative Usability Evaluation

### Traceability Requirements
- All software requirements must have test protocols
- All software requirements must have risk analysis

## Document Status

All documents in this repository are fully written with approved status:

| Category | Documents | Count |
|----------|-----------|-------|
| User Needs | UN-001, UN-002 | 2 |
| Product Requirements | PRS-001 through PRS-004 | 4 |
| Software Requirements | SRS-001 through SRS-006 | 6 |
| Architecture | HLD-001 | 1 |
| Design | SDD-001 | 1 |
| Test Protocols | TP-001 through TP-004 | 4 |
| Test Reports | TR-001 through TR-004, TR-PEN-001 | 5 |
| Risk Management Plan | RMP-001 | 1 |
| Software Development Plan | DEV-PLAN-001 | 1 |
| Software Risks | RISK-SW-001, HAZ-SW-001 | 2 |
| SOUP Register | SOUP-001 | 1 |
| Cybersecurity Plan | CSPLAN-001 | 1 |
| Security Risks | RISK-SEC-001, HAZ-SEC-001 | 2 |
| SBOM | SBOM-001 | 1 |
| Clinical Evaluation | CEP-001, CER-001 | 2 |
| Post-Market Surveillance | PMS-001 | 1 |
| Labeling | LBL-001 | 1 |
| Hazardous Situations | HS-001 through HS-003 | 3 |
| Harms | HARM-001 through HARM-003 | 3 |
| Usability | UEP-001, US-001, US-002, TA-001 through TA-003, FE-001, SE-001, RISK-US-001 | 9 |
| **Total** | | **51** |

## Continuous Integration

The `.github/workflows/device-validate.yml` workflow runs automatically on:

- **Pull requests** touching `docs/**` - validates document structure, frontmatter, and traceability links
- **Releases** - exports the Technical File for regulatory submission

The workflow uses [PactoSigna/qms-actions](https://github.com/PactoSigna/qms-actions) for validation.

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
> "Act as a Risk Management Engineer. Review RISK-SW-001 and identify 3 additional software failure modes for the detection algorithm. Create new risk documents following the same format."

**Generate test protocols:**
> "Act as a V&V Engineer. Based on PRS-001 through PRS-004, generate detailed test protocols with preconditions, steps, and expected results. Ensure full requirements coverage."

## License

This sample repository is provided under the MIT License for educational and commercial use.

---

*Built for [PactoSigna](https://pactosigna.com) - AI-native Quality Management for Medical Device Software*
