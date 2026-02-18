---
type: anomaly
id: ANOM-002
title: TLS certificate pinning bypass on Android 14
status: approved
category: security_vulnerability
severity: critical
disposition: resolved
affected_version: '1.2.0'
author: rune@ords.io
reviewers:
  - engineering
  - quality
approvers:
  - engineering
---

# ANOM-002: TLS certificate pinning bypass on Android 14

## Description

A change in Android 14's network security configuration handling caused the application's certificate pinning to be silently ignored on devices running Android 14+. This potentially allowed man-in-the-middle attacks on the communication channel between the mobile app and the cloud API.

## Affected Components

- React Native networking layer (SOUP-02)
- Firebase Auth (SOUP-03)
- API communication module

## Discovery

Identified during routine security testing (penetration test cycle Q4 2025). See [TR-PEN-001](../../test/reports/TR-PEN-001.md).

## Impact Assessment

- **Patient safety**: Indirect — compromised communication could theoretically allow interception of clinical data in transit.
- **Data confidentiality**: High — PHI could be intercepted by an attacker on the same network.
- **Regulatory**: Reportable under IEC 81001-5-1. Disclosed in CSPLAN-001 security advisory.

## Resolution

Updated the certificate pinning implementation to use the Android 14-compatible `NetworkSecurityConfig` API with explicit pin set declarations. Added runtime verification that pinning is active via a startup self-test.

## Verification

- Penetration test confirms certificate pinning is enforced on Android 14, 15 devices
- No regression on Android 12, 13 devices
- See [RISK-SEC-001](../../cybersecurity/risks/RISK-SEC-001.md) for updated risk assessment
