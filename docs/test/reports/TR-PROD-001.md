---
type: test_report
id: TR-PROD-001
title: "Production Deployment Verification — v2.1.0"
status: example
author: rune@ords.io
reviewers:
  - engineering
approvers:
  - quality
release_version: "2.1.0"
test_phase: production
---

# Production Deployment Verification: CardioSense v2.1.0

> **Note:** This is an example document with `status: example`. It will appear in the document browser for reference but will not be included in release reviews. Copy this file and change `status` to `draft` to create your own production test report.

**Executes:** [TP-001](../protocols/TP-001.md)
**Release Version:** v2.1.0
**Test Phase:** Production

## Test Environment

- Production cluster: `eu-west-1` (primary)
- API version: v2.1.0 (build 2847)
- Database: PostgreSQL 15.4
- Test date: 2026-02-20

## Test Results

| Test Case | Description | Expected | Actual | Status |
|-----------|-------------|----------|--------|--------|
| PROD-TC-001 | Health check endpoint responds | 200 OK in <100ms | 200 OK in 23ms | PASS |
| PROD-TC-002 | AF detection pipeline processes sample ECG | Classification within 5s | Classification in 1.2s | PASS |
| PROD-TC-003 | Alert notification delivered to clinician | Notification within 15s | Notification in 8.4s | PASS |
| PROD-TC-004 | Data export generates valid PDF | Valid PDF with correct headers | Valid PDF generated | PASS |
| PROD-TC-005 | Database migration applied cleanly | No errors, indexes present | Migration successful | PASS |

## Summary

All production verification test cases passed. The deployment is confirmed operational and meets specified performance thresholds. No anomalies detected during the 24-hour burn-in monitoring period.

**Verdict:** PASS — Production deployment verified.
