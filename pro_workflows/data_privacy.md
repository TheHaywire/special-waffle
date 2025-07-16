# Pro Workflows: Data Privacy

## 1. Automated Data Discovery & Classification
**Problem:** Sensitive data is often scattered and untracked, leading to privacy risks and compliance failures.

**Workflow:**
```mermaid
flowchart TD
    A[Data Sources] --> B[Discovery Tool (OpenDLP/Sniffles)]
    B -->|Scan| C[Classification Engine]
    C -->|Label| D[Data Inventory]
    D -->|Report| E[Privacy/Compliance Team]
```
**Tools:** OpenDLP, Sniffles, Apache Atlas, DataSunrise, Elastic Security

**Automation/AI Tips:**
- Schedule regular automated scans for new/changed data
- Use LLMs to interpret scan results and flag high-risk data

**Metrics:** 95%+ sensitive data coverage, reduced unknown data stores

**References:** OpenDLP docs, Apache Atlas, DataSunrise

---

## 2. Data Subject Access Request (DSAR) Automation
**Problem:** Manual DSAR handling is slow, error-prone, and risks non-compliance with privacy laws.

**Workflow:**
```mermaid
flowchart TD
    A[DSAR Received] --> B[DSAR Portal/Intake]
    B -->|Trigger| C[Automated Data Search]
    C -->|Results| D[Review/Redact]
    D -->|Fulfill/Respond| E[Data Subject]
```
**Tools:** OneTrust, Osano, OpenDLP, custom scripts

**Automation/AI Tips:**
- Automate data search and redaction for DSARs
- Use LLMs to draft responses and check for sensitive info

**Metrics:** 90%+ DSARs fulfilled on time, reduced manual effort

**References:** OneTrust DSAR, Osano, GDPR guidelines

---

## 3. Privacy Policy Enforcement & Monitoring
**Problem:** Privacy policies are often unenforced, leading to accidental data exposure or misuse.

**Workflow:**
```mermaid
flowchart TD
    A[Policy Definition] --> B[Policy Engine (OPA/Apache Ranger)]
    B -->|Enforce| C[Data Access]
    C -->|Monitor| D[Audit Logs]
    D -->|Alert| E[Privacy/Compliance Team]
```
**Tools:** Open Policy Agent, Apache Ranger, DataSunrise, Elastic Security

**Automation/AI Tips:**
- Automate policy enforcement and real-time monitoring
- Use LLMs to analyze audit logs for privacy violations

**Metrics:** 100% policy coverage, reduced privacy incidents

**References:** Open Policy Agent, Apache Ranger, DataSunrise 