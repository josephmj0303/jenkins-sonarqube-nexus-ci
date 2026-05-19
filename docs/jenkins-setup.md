# Jenkins Setup Documentation

## Overview

Jenkins is used as the Continuous Integration server for automating build, test, analysis, and artifact upload processes.

---

# Server Details

| Component | Value |
|---|---|
| OS | Ubuntu |
| Java Version | OpenJDK 21 |
| Jenkins Version | Latest Stable |
| Port | 8080 |

---

# Jenkins Installation Steps

## Update Packages

```bash
sudo apt update
```

---

## Install Java

```bash
sudo apt install -y openjdk-21-jdk wget
```

Verify Java:

```bash
java -version
```

---

## Add Jenkins Repository Key

```bash
sudo install -d -m 0755 /etc/apt/keyrings

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
```

---

## Add Jenkins Repository

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

---

## Install Jenkins

```bash
sudo apt update
sudo apt install -y jenkins
```

---

## Start Jenkins Service

```bash
sudo systemctl enable --now jenkins
```

Verify Status:

```bash
sudo systemctl status jenkins
```

---

# Jenkins Access

Default URL:

```text
http://<JENKINS_SERVER_IP>:8080
```

---

# Plugins Installed

- Pipeline
- Git
- Maven Integration
- SonarQube Scanner
- Slack Notification
- Stage View
- Nexus Artifact Uploader

---

# Jenkins Pipeline Stages

- Checkout SCM
- Tool Install
- Build
- Test
- Checkstyle Analysis
- SonarQube Analysis
- Quality Gate
- Upload Artifact
- Notifications

---

# Screenshots

Refer:
- `/screenshots/pipeline-stages.jpg`
- `/screenshots/pipeline-success.jpg`

