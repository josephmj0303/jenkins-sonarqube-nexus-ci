# Troubleshooting Guide

## Jenkins Issues

---

### Jenkins Service Not Starting

Check service status:

```bash
sudo systemctl status jenkins
```

View logs:

```bash
sudo journalctl -u jenkins
```

---

### Jenkins Port 8080 Not Accessible

Check firewall/security group rules.

Verify port:

```bash
sudo netstat -tulnp | grep 8080
```

---

# SonarQube Issues

---

### SonarQube Fails to Start

Check logs:

```bash
sudo journalctl -u sonarqube
```

Common Cause:
- vm.max_map_count not configured
- insufficient memory

---

### PostgreSQL Connection Failure

Verify PostgreSQL service:

```bash
sudo systemctl status postgresql
```

Test DB connection:

```bash
psql -U sonar -d sonarqube
```

---

### Quality Gate Failed

Possible Reasons:
- Code smells
- Bugs
- Vulnerabilities
- Coverage threshold not met

Review SonarQube dashboard for detailed analysis.

---

# Nexus Issues

---

### Nexus Service Not Starting

Check logs:

```bash
sudo journalctl -u nexus
```

Verify Java:

```bash
java -version
```

---

### Artifact Upload Failed

Verify:
- Nexus credentials
- Repository URL
- Jenkins Nexus plugin configuration

---

# Webhook Issues

---

### GitHub Webhook Not Triggering Jenkins

Check:
- Webhook URL
- GitHub delivery logs
- Jenkins GitHub trigger option
- Public accessibility of Jenkins

---

# Slack Notification Issues

---

### Slack Alerts Not Working

Verify:
- Slack webhook URL
- Jenkins Slack plugin configuration
- Network connectivity

---

# Useful Commands

## Service Status

```bash
systemctl status jenkins
systemctl status sonarqube
systemctl status nexus
```

---

## Port Validation

```bash
netstat -tulnp
```

---

## Restart Services

```bash
sudo systemctl restart jenkins
sudo systemctl restart sonarqube
sudo systemctl restart nexus
```

