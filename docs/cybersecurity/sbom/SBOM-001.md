---
type: sbom
id: SBOM-001
title: Software Bill of Materials
status: approved
author: rune@ords.io
reviewers:
  - security
approvers:
  - quality
---

# Software Bill of Materials — CardioSense

## Purpose

This SBOM provides a complete inventory of all software components, libraries, and dependencies used in CardioSense. It supports vulnerability monitoring per IEC 81001-5-1:2021 and FDA premarket cybersecurity guidance.

## Component Inventory

### Detection Engine (Python)

| Component | Version | License | CVE Status |
|-----------|---------|---------|------------|
| TensorFlow | 2.15.0 | Apache 2.0 | No active CVEs |
| NumPy | 1.26.3 | BSD 3-Clause | No active CVEs |
| SciPy | 1.12.0 | BSD 3-Clause | No active CVEs |
| pandas | 2.1.4 | BSD 3-Clause | No active CVEs |
| h5py | 3.10.0 | BSD 3-Clause | No active CVEs |

### Mobile Application (React Native)

| Component | Version | License | CVE Status |
|-----------|---------|---------|------------|
| React Native | 0.73.4 | MIT | No active CVEs |
| React | 18.2.0 | MIT | No active CVEs |
| react-navigation | 6.1.9 | MIT | No active CVEs |
| react-native-ble-plx | 3.1.2 | Apache 2.0 | No active CVEs |
| react-native-encrypted-storage | 4.0.3 | MIT | No active CVEs |

### Cloud Backend (Node.js)

| Component | Version | License | CVE Status |
|-----------|---------|---------|------------|
| Express.js | 4.18.2 | MIT | No active CVEs |
| Firebase Admin SDK | 12.0.0 | Apache 2.0 | No active CVEs |
| jsonwebtoken | 9.0.2 | MIT | No active CVEs |
| helmet | 7.1.0 | MIT | No active CVEs |
| cors | 2.8.5 | MIT | No active CVEs |

## License Compliance

All components use permissive open-source licenses (Apache 2.0, MIT, BSD). No copyleft (GPL) dependencies are included in production builds.

## Vulnerability Monitoring

- **Automated scanning**: Dependabot alerts enabled on all repositories
- **Review cadence**: Security team reviews CVE feeds weekly
- **Escalation**: Critical CVEs (CVSS >= 9.0) trigger immediate assessment per [CSPLAN-001](../plans/CSPLAN-001.md)
- **Patching SLA**: Critical within 30 days, High within 90 days
