---
type: cybersecurity_plan
id: CSPLAN-001
title: Cybersecurity Plan
status: approved
author: rune@ords.io
reviewers:
  - security
approvers:
  - quality
---

# Cybersecurity Plan — CardioSense

## Scope

This plan defines the cybersecurity risk management process for CardioSense per IEC 81001-5-1:2021. It covers threat modeling, secure development practices, vulnerability management, and incident response for all software components that process, store, or transmit patient health data.

## Applicable Standards

| Standard | Scope |
|----------|-------|
| IEC 81001-5-1:2021 | Health software security — product lifecycle |
| OWASP Top 10 | Web and API security baseline |
| NIST Cybersecurity Framework | Risk management structure |
| FDA Premarket Cybersecurity Guidance (2023) | Regulatory expectations for SaMD |

## Threat Modeling

CardioSense uses **STRIDE** methodology for threat identification:

| Threat Category | Example for CardioSense |
|----------------|------------------------|
| **S**poofing | Attacker impersonates clinician to access patient data |
| **T**ampering | Modification of ECG data in transit |
| **R**epudiation | Clinician denies reviewing a detection result |
| **I**nformation disclosure | Patient health data exposed via API vulnerability |
| **D**enial of service | Algorithm endpoint overwhelmed, delaying detections |
| **E**levation of privilege | Patient account gains clinician-level access |

Threat analysis results are documented in [docs/cybersecurity/risks/](../risks/).

## Secure Development Practices

1. **Secure coding standards**: OWASP guidelines for all API development
2. **Dependency scanning**: Automated CVE monitoring via SBOM ([SBOM-001](../sbom/SBOM-001.md))
3. **Code review**: All changes require security-aware peer review
4. **Static analysis**: Automated linting for common vulnerability patterns
5. **Penetration testing**: Annual third-party assessment ([TR-PEN-001](../../test/reports/TR-PEN-001.md))

## Data Protection

| Data Category | Protection Measure | Standard |
|--------------|-------------------|----------|
| ECG recordings | AES-256 encryption at rest, TLS 1.3 in transit | SRS-006 |
| Patient PII | Encrypted storage, role-based access control | SRS-005 |
| Authentication tokens | Short-lived JWTs, secure refresh mechanism | SRS-005 |
| Audit logs | Immutable append-only storage | 21 CFR Part 11 |

## Vulnerability Management

- **Monitoring**: Continuous CVE feeds for all SOUP components
- **Triage**: Security team assesses impact within 48 hours of disclosure
- **Patching**: Critical vulnerabilities patched within 30 days; high within 90 days
- **Disclosure**: Coordinated vulnerability disclosure process for externally reported issues

## Incident Response

1. **Detection**: Automated alerting on anomalous API patterns
2. **Containment**: Isolate affected components, revoke compromised credentials
3. **Investigation**: Root cause analysis, impact assessment
4. **Recovery**: Deploy patched version, verify integrity
5. **Reporting**: Notify affected users and regulators per MDR Art. 87 if applicable
