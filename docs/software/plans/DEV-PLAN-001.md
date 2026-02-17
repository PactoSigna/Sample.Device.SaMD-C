---
type: software_development_plan
id: DEV-PLAN-001
title: Software Development Plan
status: approved
author: rune@ords.io
reviewers:
  - engineering
approvers:
  - quality
---

# Software Development Plan — CardioSense

## Scope

This plan defines the software development lifecycle for CardioSense, a Class C SaMD for atrial fibrillation detection. It applies to all software items including the detection algorithm, mobile application, cloud backend, and clinician web portal.

## Software Safety Classification

Per IEC 62304:2015 clause 4.3, CardioSense is classified as **Class C** (can result in death or serious injury). This classification drives the rigor of all lifecycle activities defined in this plan.

## Development Lifecycle

CardioSense follows an iterative development lifecycle with the following phases:

| Phase | Activities | Outputs |
|-------|-----------|---------|
| Planning | Requirements elicitation, risk identification | This plan, RMP-001 |
| Requirements | User needs, product requirements, software requirements | UN-xxx, PRS-xxx, SRS-xxx |
| Architecture | High-level design, interface definitions | HLD-001 |
| Detailed Design | Module design, algorithm specification | SDD-001 |
| Implementation | Coding, unit testing, code review | Source code, unit test results |
| Verification | Integration testing, system testing | TP-xxx protocols, TR-xxx reports |
| Validation | Usability evaluation, clinical evaluation | SE-001, CER-001 |
| Release | Release packaging, regulatory submission | Release record |

## Development Tools

| Tool | Purpose | Qualification |
|------|---------|--------------|
| Python 3.11 | Algorithm development | Validated via test suite |
| TensorFlow 2.15 | ML model training and inference | SOUP — see SOUP-001 |
| React Native 0.73 | Mobile application | SOUP — see SOUP-001 |
| Firebase | Cloud backend and authentication | SOUP — see SOUP-001 |
| Vitest | Unit testing framework | Industry-standard |
| Playwright | System/integration testing | Industry-standard |

## SOUP Management

All Software of Unknown Provenance is documented in [SOUP-001](../soup/SOUP-001.md). SOUP items are:
- Evaluated for risk contribution per IEC 62304 clause 8.1
- Version-locked with pinned dependencies
- Monitored for security vulnerabilities via SBOM tracking ([SBOM-001](../../cybersecurity/sbom/SBOM-001.md))
- Verified through integration testing

## Configuration Management

- **Version control**: Git (GitHub)
- **Branching model**: Feature branches with pull request review
- **Change control**: All changes require review and approval before merge
- **Traceability**: Document IDs link requirements to design to test to risk

## Problem Resolution

Software anomalies discovered during development or post-market are tracked as GitHub Issues and resolved through the standard change control process. Critical safety anomalies trigger immediate risk reassessment per [RMP-001](../../risk/plans/RMP-001.md).
