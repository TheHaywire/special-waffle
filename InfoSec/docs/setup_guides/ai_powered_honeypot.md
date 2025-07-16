# Setup Guide: AI-Powered Honeypot Deployment

---

## Overview
This guide explains how to deploy an AI-powered honeypot using open-source tools such as prickly-pete, Cowrie, or a custom integration with LLMs. The honeypot will dynamically adapt its behavior to deceive attackers and collect threat intelligence.

---

## Prerequisites
- Linux server or VM (Ubuntu recommended)
- Python 3.x
- Docker (optional, for containerized deployment)
- Basic networking knowledge
- (Optional) Access to an LLM API (e.g., OpenAI, local LLM)

---

## Step 1: Choose Your Honeypot Solution
- **prickly-pete**: Modular, AI-driven honeypot suite ([GitHub](https://github.com/chriskiehl/prickly-pete))
- **Cowrie**: Popular SSH/Telnet honeypot ([GitHub](https://github.com/cowrie/cowrie))
- **Custom LLM Integration**: Use an LLM to generate dynamic responses or deception strategies

---

## Step 2: Deploy prickly-pete (Example)
```bash
git clone https://github.com/chriskiehl/prickly-pete.git
cd prickly-pete
pip install -r requirements.txt
python run.py
```
- Edit `config.yaml` to customize services, ports, and AI/LLM integration.

---

## Step 3: (Alternative) Deploy Cowrie
```bash
git clone https://github.com/cowrie/cowrie.git
cd cowrie
python3 -m venv cowrie-env
source cowrie-env/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
cp etc/cowrie.cfg.dist etc/cowrie.cfg
bin/cowrie start
```
- Edit `etc/cowrie.cfg` to configure ports, logging, and fake credentials.

---

## Step 4: Integrate LLM for Dynamic Deception (Optional)
- Use a Python script to call an LLM API and generate responses based on attacker input.
- Example: Modify Cowrie or prickly-pete to call an LLM for SSH/Telnet session responses.

---

## Step 5: Collect and Analyze Logs
- Logs are stored locally or can be forwarded to a SIEM (e.g., ELK, Wazuh).
- Analyze logs for attacker behavior, tools, and TTPs (tactics, techniques, procedures).

---

## Troubleshooting Tips
- Ensure required ports are open and not blocked by firewalls.
- Run honeypots in isolated or monitored environments to avoid risk to production systems.
- Regularly update honeypot software and dependencies.
- For LLM integration, handle API keys securely and monitor usage.

---

## References
- [prickly-pete GitHub](https://github.com/chriskiehl/prickly-pete)
- [Cowrie GitHub](https://github.com/cowrie/cowrie)
- [OpenAI API Docs](https://platform.openai.com/docs/) 