# GitHub Webhook Configuration

## Overview

GitHub webhooks are configured to automatically trigger Jenkins pipelines whenever code changes are pushed to the repository.

---

# Workflow

Developer Push
→ GitHub Repository
→ Webhook Trigger
→ Jenkins Pipeline Execution

---

# Jenkins Configuration

## Install Required Plugins

- GitHub Integration Plugin
- Git Plugin

---

# Configure Jenkins Job

Enable:

```text
GitHub hook trigger for GITScm polling
```

---

# GitHub Webhook Setup

Navigate to:

```text
GitHub Repository → Settings → Webhooks
```

Add webhook:

| Field | Value |
|---|---|
| Payload URL | http://<JENKINS_IP>:8080/github-webhook/ |
| Content Type | application/json |

---

# Events Configured

- Push Events

---

# Verify Webhook

After pushing code:
- Jenkins build should trigger automatically
- Webhook delivery should show HTTP 200 response

---

# Troubleshooting

## Webhook Not Triggering

Check:
- Jenkins public accessibility
- Security group inbound rules
- GitHub webhook delivery logs
- Jenkins GitHub plugin installation

