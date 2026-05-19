# SonarQube Setup Documentation

## Overview

SonarQube is integrated into the CI pipeline for static code analysis and quality gate enforcement.

---

# Server Details

| Component | Value |
|---|---|
| OS | Ubuntu |
| SonarQube Version | 9.9.8 |
| Database | PostgreSQL |
| Java Version | OpenJDK 17 |
| Port | 9000 |

---

# Kernel & System Configuration

Update kernel limits for Elasticsearch requirements.

```bash
vm.max_map_count=262144
fs.file-max=65536
```

Update security limits:

```bash
sonarqube   -   nofile   65536
sonarqube   -   nproc    4096
```

---

# Install Java

```bash
sudo apt-get install openjdk-17-jdk -y
```

---

# Install PostgreSQL

```bash
sudo apt install postgresql postgresql-contrib -y
```

Enable PostgreSQL:

```bash
sudo systemctl enable postgresql.service
sudo systemctl start postgresql.service
```

---

# Configure Database

Create SonarQube database and user.

```sql
CREATE DATABASE sonarqube OWNER sonar;
```

---

# Install SonarQube

Download SonarQube:

```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.9.8.100196.zip
```

Extract:

```bash
sudo unzip sonarqube-9.9.8.100196.zip -d /opt/
```

---

# Configure SonarQube

Update:

```bash
/opt/sonarqube/conf/sonar.properties
```

Important properties:

```properties
sonar.jdbc.username=sonar
sonar.jdbc.password=******
sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube
sonar.web.port=9000
```

---

# Configure Systemd Service

Create:

```bash
/etc/systemd/system/sonarqube.service
```

Enable service:

```bash
sudo systemctl daemon-reload
sudo systemctl enable sonarqube
sudo systemctl start sonarqube
```

---

# Configure Nginx Reverse Proxy

Nginx is configured as a reverse proxy for SonarQube.

Proxy Port:
- 80 → 9000

---

# Access SonarQube

```text
http://<SONARQUBE_SERVER_IP>:9000
```

---

# SonarQube Features Used

- Code Smells Detection
- Bug Analysis
- Vulnerability Scanning
- Quality Gates
- Security Hotspots

---

# Screenshots

Refer:
- `/screenshots/sonarqube-main.jpg`
- `/screenshots/sonarqube-status.jpg`

