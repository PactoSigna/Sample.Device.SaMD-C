---
id: HARM-003
title: Patient Data Breach
status: approved
severity: 3
author: rune@ords.io
reviewers:
  - quality
approvers:
  - quality
---

# Harm: Patient Data Breach

## Description

Patient detection records -- including ECG data, AFib detection results, and personal health information -- are exposed to unauthorized parties through exploitation of system vulnerabilities.

## Severity Assessment

**Severity Level: 3 (Serious)**

Potential outcomes:

- Patient health data exposed to unauthorized parties
- Regulatory violations (HIPAA breach notification, GDPR data breach reporting)
- Loss of patient trust in the device and healthcare provider
- Legal liability for the manufacturer and deploying organization
- Financial penalties from regulatory authorities

## Regulatory Consequences

A breach of patient detection records triggers mandatory reporting under multiple regulatory frameworks:

- **HIPAA** (US): Breach notification to affected individuals within 60 days; HHS notification; potential civil monetary penalties up to $1.5M per violation category per year
- **GDPR** (EU): Supervisory authority notification within 72 hours; data subject notification if high risk; fines up to 4% of annual global turnover
- **MDR** (EU): Reportable as a serious incident if the breach compromises device safety or performance data

## Applicable Regulatory Guidance

- ISO 14971:2019 Annex D - Severity classification
- IEC 81001-5-1 - Health software cybersecurity
- FDA Guidance: Postmarket Management of Cybersecurity in Medical Devices
