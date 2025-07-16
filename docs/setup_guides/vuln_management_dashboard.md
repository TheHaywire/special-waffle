# Setup Guide: Open-Source Vulnerability Management Dashboard

---

## Overview
This guide explains how to deploy and use an open-source vulnerability management dashboard, such as CVElk, DefectDojo, or a custom dashboard. These tools help track, prioritize, and remediate vulnerabilities across your environment.

---

## Prerequisites
- Linux server, VM, or desktop (Ubuntu recommended)
- 4+ GB RAM, 2+ CPUs
- Docker (recommended) or root access for manual install
- Python 3.x (for DefectDojo or custom scripts)
- Access to vulnerability scan results (CSV, JSON, or API)

---

## Step 1: Choose Your Tool
- **CVElk**: CVE dashboard using ELK stack ([GitHub](https://github.com/nu11secur1ty/CVElk))
- **DefectDojo**: Comprehensive vulnerability management platform ([GitHub](https://github.com/DefectDojo/django-DefectDojo))
- **Custom Dashboard**: Build your own with Python (Flask/Django), Node.js, or ELK

---

## Step 2: Deploy CVElk (Example)
```bash
git clone https://github.com/nu11secur1ty/CVElk.git
cd CVElk
sudo docker-compose up -d
```
- Access the dashboard at http://localhost:5601 (Kibana)

---

## Step 3: Deploy DefectDojo (Example)
```bash
git clone https://github.com/DefectDojo/django-DefectDojo.git
docker compose -f docker/docker-compose.yml up
```
- Access DefectDojo at http://localhost:8080 (default credentials: admin@defectdojo.local / admin)

---

## Step 4: Import Vulnerability Data
- Import scan results from tools like OpenVAS, Nessus, or custom scripts
- Use built-in importers or APIs to upload findings

---

## Step 5: Track, Prioritize, and Remediate
- Use dashboards to view vulnerabilities by severity, asset, or status
- Assign remediation tasks to IT/SecOps
- Track progress and generate reports for compliance

---

## Troubleshooting Tips
- Ensure required ports (5601, 8080, etc.) are open
- Check Docker/container logs for errors if services do not start
- For large environments, increase VM resources and storage
- Regularly update vulnerability feeds and tool versions

---

## References
- [CVElk GitHub](https://github.com/nu11secur1ty/CVElk)
- [DefectDojo Docs](https://defectdojo.github.io/django-DefectDojo/) 