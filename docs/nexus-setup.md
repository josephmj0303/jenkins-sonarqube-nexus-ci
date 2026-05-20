# Nexus Repository Setup Documentation

## Overview

Nexus Repository Manager is used for storing and managing build artifacts generated from Jenkins pipelines.

---

# Server Details

| Component | Value |
|---|---|
| OS | Amazon Linux |
| Nexus Version | 3.78.0-14 |
| Java Version | Amazon Corretto 17 |
| Port | 8081 |

---

# Install Java

```bash
sudo yum install -y java-17-amazon-corretto-devel wget
```

Verify:

```bash
java -version
```

---

# Download Nexus

```bash
wget https://download.sonatype.com/nexus/3/nexus-unix-x86-64-3.78.0-14.tar.gz
```

Extract package:

```bash
tar xzvf nexus.tar.gz
```

---

# Create Nexus Directories

```bash
mkdir -p /opt/nexus/
```

---

# Create Nexus User

```bash
useradd nexus
```

Assign ownership:

```bash
chown -R nexus:nexus /opt/nexus
```

---

# Configure Nexus Service

Create:

```bash
/etc/systemd/system/nexus.service
```

Enable and start service:

```bash
sudo systemctl daemon-reload
sudo systemctl start nexus
sudo systemctl enable nexus
```

---

# Nexus Repository Types Used

- Maven Hosted Repository
- Maven Proxy Repository
- Maven Group Repository

---

# Artifact Upload Flow

1. Jenkins builds WAR artifact
2. Maven packages application
3. Jenkins uploads artifact to Nexus
4. Nexus stores versioned artifacts

---

# Access Nexus

```text
http://<NEXUS_SERVER_IP>:8081
```

---

# Screenshots

Refer:
- `/screenshots/nexus-home.jpg`
- `/screenshots/nexus-repo.jpg`

