# Setup Guide: Open-Source Threat Intelligence Platform (TIP) Deployment

---

## Overview
This guide explains how to deploy an open-source threat intelligence platform (TIP) using MISP, OpenCTI, or a custom solution. The TIP will aggregate, correlate, and analyze threat data from multiple sources, providing actionable intelligence for defenders.

---

## Prerequisites
- Linux server or VM (Ubuntu recommended)
- 4+ GB RAM, 2+ CPUs (more for production)
- Docker (recommended) or root access for manual install
- Python 3.x (for OpenCTI or custom scripts)
- Basic knowledge of Linux and networking

---

## Step 1: Choose Your TIP Solution
- **MISP**: Mature, widely used threat intelligence platform ([GitHub](https://github.com/MISP/MISP))
- **OpenCTI**: Modern, graph-based TIP ([GitHub](https://github.com/OpenCTI-Platform/opencti))
- **Custom TIP**: Build your own with Python, MongoDB, and visualization tools

---

## Step 2: Quick Start with Docker Compose

### Example: Deploy MISP
```bash
git clone https://github.com/MISP/misp-docker.git
cd misp-docker
sudo docker compose up -d
```
- Access MISP at http://localhost:8080 (default credentials: admin@admin.test/admin)

### Example: Deploy OpenCTI
```bash
git clone https://github.com/OpenCTI-Platform/docker.git opencti-docker
cd opencti-docker
sudo docker compose up -d
```
- Access OpenCTI at http://localhost:8080 (default credentials: admin@opencti.io/admin)

---

## Step 3: Configure Data Sources & Feeds
- Ingest threat feeds (OSINT, commercial, custom) via built-in connectors or API.
- Enable integrations with MISP, OpenCTI, or custom scripts for:
  - Malware hashes
  - Phishing URLs
  - Vulnerability data (CVE)
  - Dark web monitoring

---

## Step 4: Correlate, Analyze, and Visualize
- Use the TIP dashboard to search, correlate, and visualize indicators of compromise (IOCs).
- Set up alerts for new or high-severity threats.
- Integrate with SIEM/SOAR for automated response.

---

## Step 5: Share Intelligence
- Configure sharing groups and permissions for collaboration with partners or community.
- Use built-in export/import features (STIX, CSV, JSON).

---

## Troubleshooting Tips
- Check Docker/container logs for errors if services do not start.
- Ensure required ports (8080, 443, 80, etc.) are open.
- For large deployments, increase VM resources and storage.
- Review TIP documentation for tuning, scaling, and security best practices.

---

## References
- [MISP Docs](https://www.misp-project.org/documentation.html)
- [OpenCTI Docs](https://www.opencti.io/docs/)
- [MISP GitHub](https://github.com/MISP/MISP)
- [OpenCTI GitHub](https://github.com/OpenCTI-Platform/opencti) 