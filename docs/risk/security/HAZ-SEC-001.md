---
id: HAZ-SEC-001
title: Attacker Exploits API to Access Patient Records
status: approved
author: rune@ords.io
reviewers:
  - quality
  - security
approvers:
  - engineering
  - quality
analyzes: SRS-005
---

# Hazard: Attacker Exploits API to Access Patient Records

## Description

An unauthorized actor exploits an API vulnerability or weak authentication mechanism to access patient detection records, compromising data confidentiality.

## sFMEA Analysis

**Failure Mode:** Unauthorized API access returns patient detection data

**Cause:**

- Missing or insufficient authentication on API endpoints
- Session token leakage or weak token generation
- Injection vulnerability in query parameters

**Detection Method:**

- Automated penetration testing during each release cycle
- Runtime API access logging and anomaly detection
- Static analysis for injection vulnerabilities
- Security review during design and code review phases

## Hazardous Situations

This hazard can lead to:

- [HS-001](../situations/HS-001.md) - Patient with undetected AFib does not seek treatment
