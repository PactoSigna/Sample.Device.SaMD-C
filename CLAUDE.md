# CLAUDE.md

## Project Overview

CardioSense is a hypothetical Class C SaMD (Software as a Medical Device) for cardiac arrhythmia detection. This repository contains its Technical File / Design History File (DHF), structured as a sample for [PactoSigna](https://pactosigna.com).

The device analyzes ECG data to detect atrial fibrillation (AFib). The documentation covers IEC 62304 (software lifecycle), ISO 14971 (risk management), IEC 62366 (usability engineering), and IEC 81001-5-1 (cybersecurity).

## Folder to Document Type Mapping

| Folder | Document Type | ID Prefix | Example |
|--------|--------------|-----------|---------|
| `docs/user-needs/` | User Need | `UN-` | UN-001 |
| `docs/product-requirements/` | Product Requirement | `PRS-` | PRS-001 |
| `docs/software-requirements/` | Software Requirement | `SRS-` | SRS-001 |
| `docs/architecture/` | High-Level Design | `HLD-` | HLD-001 |
| `docs/design/` | Software Design | `SDD-` | SDD-001 |
| `docs/test/protocols/` | Test Protocol | `TP-` | TP-001 |
| `docs/test/reports/` | Test Report | `TR-` | TR-001 |
| `docs/risk/plans/` | Risk Management Plan | `RMP-` | RMP-001 |
| `docs/risk/situations/` | Hazardous Situation | `HS-` | HS-001 |
| `docs/risk/harms/` | Harm | `HARM-` | HARM-001 |
| `docs/software/plans/` | Software Development Plan | `DEV-PLAN-` | DEV-PLAN-001 |
| `docs/software/risks/` | Software Risk / Hazard | `RISK-SW-`, `HAZ-SW-` | RISK-SW-001 |
| `docs/software/soup/` | SOUP Register | `SOUP-` | SOUP-001 |
| `docs/cybersecurity/plans/` | Cybersecurity Plan | `CSPLAN-` | CSPLAN-001 |
| `docs/cybersecurity/risks/` | Security Risk / Hazard | `RISK-SEC-`, `HAZ-SEC-` | HAZ-SEC-001 |
| `docs/cybersecurity/sbom/` | Software Bill of Materials | `SBOM-` | SBOM-001 |
| `docs/clinical/` | Clinical Evaluation Plan / Report | `CEP-`, `CER-` | CEP-001 |
| `docs/post-market/` | Post-Market Surveillance Plan | `PMS-` | PMS-001 |
| `docs/labeling/` | Labeling / IFU | `LBL-` | LBL-001 |
| `docs/usability/` | Usability Engineering Plan | `UEP-` | UEP-001 |
| `docs/usability/use-specifications/` | Use Specification | `US-` | US-001 |
| `docs/usability/task-analyses/` | Task Analysis | `TA-` | TA-001 |
| `docs/usability/evaluations/` | Usability / Summative Evaluation | `UE-`, `SE-`, `FE-` | SE-001 |
| `docs/usability/risks/` | Usability Risk | `RISK-US-` | RISK-US-001 |

## Frontmatter Schema

Every document has YAML frontmatter. Required fields:

```yaml
---
id: UN-001                  # Unique document identifier (matches filename without .md)
title: Document Title       # Human-readable title
status: approved            # One of: draft, in_review, approved, obsolete
author: user@example.com    # Author email address
reviewers:                  # List of reviewer roles or emails
  - quality
approvers:                  # List of approver roles or emails
  - quality
---
```

Optional type-specific fields:

| Field | Used By | Example |
|-------|---------|---------|
| `derives_from` | PRS, SRS | `derives_from: UN-001` |
| `implements` | HLD, SDD | `implements: SRS-001` |
| `verified_by` | PRS, SRS | `verified_by: TP-001` |
| `analyzes` | RISK, HAZ | `analyzes: SRS-005` |
| `mitigates` | SRS, PRS | `mitigates: HAZ-SW-001` |
| `severity` | HARM | `severity: 4` |
| `probability` | HS | `probability: 3` |
| `source` | TR | `source: ../pentest-report.pdf` |

## Traceability Link Types

| Link Type | Direction | Example |
|-----------|-----------|---------|
| `derives_from` | Requirement --> User Need | PRS-001 derives from UN-001 |
| `implements` | Architecture --> Requirement | HLD-001 implements SRS-001 |
| `verified_by` | Test --> Requirement | TP-001 verifies PRS-001 |
| `mitigates` | Requirement --> Hazard | PRS-004 mitigates HAZ-SW-001 |
| `leads_to` | Hazard --> Situation | HAZ-SW-001 leads to HS-001 |
| `results_in` | Situation --> Harm | HS-001 results in HARM-001 |
| `analyzes` | Risk Assessment --> Hazard | RISK-SW-001 analyzes HAZ-SW-001 |

## Risk Chain (ISO 14971)

Risk documents follow the ISO 14971 sequence:

```
Hazard (HAZ-*) --> Hazardous Situation (HS-*) --> Harm (HARM-*)
```

- **Hazard**: A potential source of harm (e.g., algorithm fails to detect AFib)
- **Hazardous Situation**: A circumstance in which a person is exposed to a hazard (e.g., patient with undetected AFib)
- **Harm**: Physical injury or damage to health (e.g., stroke from untreated AFib)

Risk assessments (`RISK-*`) analyze the full chain and document inherent risk, controls, and residual risk using a severity x probability matrix.

## Document Status Lifecycle

```
draft --> in_review --> approved --> obsolete
```

- **draft**: Initial authoring, not yet reviewed
- **in_review**: Under review by designated reviewers
- **approved**: Reviewed and approved, part of the active Technical File
- **obsolete**: Superseded or no longer applicable

All documents in this repository are currently in `approved` status.

## Continuous Integration

`.github/workflows/device-validate.yml` runs on:

- **Pull requests** (paths: `docs/**`): Validates frontmatter, document structure, and traceability links
- **Releases**: Exports the Technical File for regulatory submission

The workflow uses `PactoSigna/qms-actions@v1` with `type: device`.

## Key Rules for Editing

1. **Document ID must match filename**: `UN-001.md` must have `id: UN-001` in frontmatter
2. **All traceability links must resolve**: If you reference `SRS-005`, the file `docs/software-requirements/SRS-005.md` must exist
3. **Maintain the risk chain**: Every Hazardous Situation must link to at least one Harm; every Hazard must link to at least one Hazardous Situation
4. **Use relative links in markdown body**: Link to other documents using relative paths (e.g., `../software-requirements/SRS-005.md`)
5. **Keep frontmatter and body consistent**: The `title` in frontmatter must match the `# Heading` in the body
