# Setup Guide: Open-Source OSINT Toolkit Deployment

---

## Overview
This guide explains how to deploy and use an open-source OSINT (Open Source Intelligence) toolkit such as SpiderFoot, theHarvester, or a custom modular toolkit. These tools help gather intelligence on domains, IPs, emails, and more for security investigations.

---

## Prerequisites
- Linux server, VM, or desktop (Ubuntu recommended)
- Python 3.x
- Docker (optional, for containerized deployment)
- Internet access (for OSINT queries)

---

## Step 1: Choose Your OSINT Toolkit
- **SpiderFoot**: Comprehensive, web-based OSINT automation ([GitHub](https://github.com/smicallef/spiderfoot))
- **theHarvester**: Lightweight, CLI-based OSINT tool ([GitHub](https://github.com/laramies/theHarvester))
- **Custom Toolkit**: Build your own with Python and modular plugins

---

## Step 2: Deploy SpiderFoot (Web UI Example)
```bash
git clone https://github.com/smicallef/spiderfoot.git
cd spiderfoot
pip install -r requirements.txt
python sf.py -l 127.0.0.1:5001
```
- Access the web UI at http://127.0.0.1:5001

---

## Step 3: Deploy theHarvester (CLI Example)
```bash
git clone https://github.com/laramies/theHarvester.git
cd theHarvester
pip install -r requirements.txt
python3 theHarvester.py -d example.com -b google
```
- Replace `example.com` with your target domain

---

## Step 4: (Optional) Build a Custom Modular Toolkit
- Use Python and libraries like `requests`, `BeautifulSoup`, and `argparse`
- Structure your toolkit with pluggable modules for domains, IPs, emails, etc.

---

## Step 5: Example Usage
- **SpiderFoot**: Create a new scan, select modules (DNS, WHOIS, social, etc.), and review results in the dashboard
- **theHarvester**: Run CLI commands to gather emails, subdomains, hosts, and more

---

## Troubleshooting Tips
- Ensure required Python dependencies are installed
- For SpiderFoot, check logs if the web UI does not start
- Some modules require API keys (e.g., Shodan, VirusTotal)—add them in the config
- Respect target site terms of service and legal boundaries

---

## References
- [SpiderFoot Docs](https://www.spiderfoot.net/documentation/)
- [theHarvester GitHub](https://github.com/laramies/theHarvester) 