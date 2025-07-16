# Setup Guide: Open-Source Phishing Simulation Platform (GoPhish)

---

## Overview
This guide explains how to deploy and use GoPhish, an open-source phishing simulation platform. GoPhish allows you to create, send, and track simulated phishing campaigns to assess and improve security awareness.

---

## Prerequisites
- Linux server or VM (Ubuntu recommended)
- 1+ GB RAM, 1+ CPU
- Docker (optional) or root access for manual install
- SMTP relay or mail server credentials (for sending emails)
- Domain name (recommended for realistic campaigns)

---

## Step 1: Download and Install GoPhish
### Option 1: Download Release
```bash
wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip
unzip gophish-v0.12.1-linux-64bit.zip
cd gophish-v0.12.1-linux-64bit
./gophish
```
- By default, the admin UI runs on https://localhost:3333 (admin:gophish)
- The phishing server runs on http://localhost:80

### Option 2: Docker
```bash
docker run --rm -p 3333:3333 -p 80:80 gophish/gophish
```

---

## Step 2: Initial Configuration
- Access the admin UI at https://<your-server-ip>:3333
- Change the default admin password
- Set up sending profiles with your SMTP server credentials
- Configure landing pages and email templates

---

## Step 3: Create and Launch a Campaign
1. Add target users/groups (CSV import supported)
2. Create an email template (use variables for personalization)
3. Set up a landing page (clone a login page or use a template)
4. Configure the sending profile (SMTP)
5. Launch the campaign and monitor results in real time

---

## Step 4: Analyze Results
- View who opened emails, clicked links, and submitted data
- Export results for reporting and awareness training

---

## Troubleshooting Tips
- Ensure ports 3333 (admin) and 80 (phishing server) are open
- Some cloud providers block outbound SMTP—use a relay or check firewall rules
- For realistic campaigns, use a domain with proper SPF/DKIM/DMARC records
- Check GoPhish logs for errors (`gophish.log`)

---

## References
- [GoPhish Docs](https://docs.getgophish.com/)
- [GoPhish GitHub](https://github.com/gophish/gophish) 