# Setup Guide: Open-Source SIEM Deployment (ELK/Wazuh/iSOC)

---

## Overview
This guide explains how to deploy an open-source SIEM (Security Information and Event Management) solution using the ELK stack (Elasticsearch, Logstash, Kibana), Wazuh, or iSOC. The SIEM will collect, store, correlate, and visualize security events from across your environment.

---

## Prerequisites
- Linux server or VM (Ubuntu recommended)
- 4+ GB RAM, 2+ CPUs (more for production)
- Docker (recommended) or root access for manual install
- Basic knowledge of Linux and networking

---

## Step 1: Choose Your SIEM Solution
- **ELK Stack**: Flexible, widely used for log management and SIEM use cases
- **Wazuh**: Adds security analytics, agent-based monitoring, and compliance to ELK
- **iSOC**: Lightweight, open-source mini-SOC ([GitHub](https://github.com/0x4D31/iSOC))

---

## Step 2: Quick Start with Docker Compose (ELK + Wazuh)

### Example: ELK Stack
```bash
git clone https://github.com/deviantony/docker-elk.git
cd docker-elk
cp .env.example .env
# (Optional) Edit .env for custom ports/resources
sudo docker-compose up -d
```
- Access Kibana at http://localhost:5601

### Example: Wazuh (with ELK)
```bash
git clone https://github.com/wazuh/wazuh-docker.git
cd wazuh-docker
sudo docker-compose -f single-node.yml up -d
```
- Access Wazuh dashboard at https://localhost:5601 (default credentials: admin/admin)

---

## Step 3: Configure Log Sources
- Install Wazuh agent or Filebeat on endpoints/servers:
```bash
# Example: Install Filebeat on Ubuntu
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.17.0-amd64.deb
sudo dpkg -i filebeat-7.17.0-amd64.deb
```
- Edit Filebeat or Wazuh agent config to point to your SIEM server.
- Enable modules for syslog, auditd, nginx, etc.

---

## Step 4: Ingest and Visualize Security Events
- Use Kibana or Wazuh dashboard to search, filter, and visualize logs.
- Set up detection rules, alerts, and dashboards for:
  - Authentication failures
  - Suspicious process execution
  - Network anomalies
  - File integrity monitoring

---

## Step 5: (Optional) Deploy iSOC Mini-SOC
```bash
git clone https://github.com/0x4D31/iSOC.git
cd iSOC
pip install -r requirements.txt
python main.py
```
- Follow prompts to ingest logs and view the dashboard.

---

## Troubleshooting Tips
- Check Docker logs (`docker logs <container>`) for errors.
- Ensure ports 9200 (Elasticsearch), 5601 (Kibana), and 1514/1515 (Wazuh) are open.
- For large environments, increase VM resources and storage.
- Review SIEM documentation for tuning and scaling.

---

## References
- [ELK Stack Docs](https://www.elastic.co/what-is/elk-stack)
- [Wazuh Docs](https://documentation.wazuh.com/)
- [iSOC GitHub](https://github.com/0x4D31/iSOC) 