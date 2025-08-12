# Jfrog-Airgapped
JFrog Container Registry (Artifactory) via RPM in an air-gapped RHEL environment,
# 🐸 JFrog Artifactory Standalone Installation on RHEL/CentOS

## 📋 Prerequisites

Before proceeding with the installation, ensure the following system requirements and configurations are in place:

### 1. System Requirements
- ✅ Minimum 4 GB RAM (8 GB recommended for production or large workloads)
- 💾 At least 50 GB of disk space (more for builds and large repositories)
- ⚙️ Multi-core processor for better performance

### 2. Operating System
- 🐧 JFrog Artifactory supports:
  - Linux (RHEL, CentOS, Ubuntu, Rocky, Alma)
  - Windows
  - macOS
- A **stable 64-bit OS** is recommended

### 3. Database Requirements (for external DB setup)
- PostgreSQL 10 or later (✅ Recommended)
- MySQL 5.7 or later
- Microsoft SQL Server 2016 or later
- Oracle 12c or later

> ℹ️ You can use the bundled PostgreSQL that comes with JFrog, or connect to an external database.

### 4. Java Development Kit (JDK)
- JFrog Artifactory requires **Java 11 or later**
- ✅ Recommended: OpenJDK 11 or OpenJDK 17

### 5. Network and Firewall Settings
- Ensure **port 8081** is open for accessing the Artifactory web UI
- Configure other required ports if using a reverse proxy, database, or Docker registry

### 6. User Permissions
- You must have **root** or **sudo** privileges to install and configure Artifactory

---

## ☕ Step 1: Install Java 17 in an Air-Gapped Environment

In an air-gapped setup, you must manually download Java RPMs and their dependencies, transfer them to the target server, and install them locally.

### 🔄 1. Download Java 17 RPM on an Internet-Enabled Machine

Use an internet-connected RHEL-based system to download the RPM for Java 17 and all its dependencies.

```bash
# Create a working directory
mkdir -p ~/java-rpms && cd ~/java-rpms

# Download Java 17 RPM and all required dependencies
dnf download --resolve --alldeps java-17-openjdk java-17-openjdk-devel

2. Transfer RPM Files to Air-Gapped Jenkins/JFrog Server
Use scp  to transfer the downloaded .rpm files:

scp *.rpm username@192.168.95.70:/opt/java/

3. Install Java RPMs Locally on the Air-Gapped Server

cd /opt/java

# Recommended method using yum localinstall
sudo yum localinstall *.rpm --disablerepo="*" --skip-broken

java -version


