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

## ☕ Step 1: Install Java 17

JFrog requires Java 11+, and we will install **OpenJDK 17**, which is fully supported and stable.

### ✅ For RHEL / CentOS / Rocky / AlmaLinux

```bash
# Update the system
sudo yum update -y

# Install OpenJDK 17
sudo yum install -y java-17-openjdk java-17-openjdk-devel

# Verify Java installation
java -version
