# Architecture Documentation

## Overview

This project implements a production-style Continuous Integration (CI) workflow using Jenkins, SonarQube, Nexus Repository, GitHub, Slack, and AWS EC2.

The pipeline automates the software delivery lifecycle from source code commit to artifact storage with integrated code quality validation.

---

# Architecture Components

## 1. GitHub
Used as the Source Code Management (SCM) platform.

Responsibilities:
- Source code hosting
- Version control
- Webhook trigger integration
- Collaboration and commit tracking

---

## 2. Jenkins
Acts as the CI orchestration server.

Responsibilities:
- Pipeline execution
- Build automation
- Test execution
- SonarQube integration
- Artifact upload to Nexus
- Slack notifications

---

## 3. SonarQube
Used for static code analysis and quality gate validation.

Responsibilities:
- Code quality analysis
- Bug detection
- Vulnerability scanning
- Code smell analysis
- Quality gate enforcement

---

## 4. Nexus Repository
Acts as the artifact repository manager.

Responsibilities:
- Artifact versioning
- WAR/JAR storage
- Build traceability
- Centralized package management

---

## 5. Slack
Used for build notifications.

Responsibilities:
- Build success alerts
- Build failure alerts
- Quality gate notifications

---

## 6. AWS EC2
Infrastructure platform hosting all services.

Instances Used:
- Jenkins Server
- SonarQube Server
- Nexus Server

---

# CI Workflow

1. Developer commits code to GitHub
2. GitHub webhook triggers Jenkins pipeline
3. Jenkins fetches source code
4. Maven build and tests are executed
5. SonarQube performs static code analysis
6. Quality gate validation is performed
7. Artifact is packaged
8. Artifact is uploaded to Nexus
9. Slack notifications are sent

---

# Architecture Diagram

Refer:
`/screenshots/architecture_diagram.png`

