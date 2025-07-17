# Pro Workflows: Data Privacy

## 1. Automated Data Discovery & Classification
**Problem:** Sensitive data is often scattered and untracked, leading to privacy risks and compliance failures.

**Workflow:**
```mermaid
flowchart TD
    subgraph DataStore
        A1[Structured Data] --> A2[Unstructured Data]
        A2 --> A3[Cloud Storage]
        A3 --> A4[Applications]
        A4 --> A5[Email]
        A5 --> A6[Backup]
    end
    subgraph Discovery
        B1[Scanners] --> B2[Content Analysis]
        B2 --> B3[Pattern Recog]
        B3 --> B4[Metadata]
        B4 --> B5[Lineage]
        B5 --> B6[Mapping]
    end
    subgraph Classify
        C1[Data Types] --> C2[Sensitivity]
        C2 --> C3[Reg Class]
        C3 --> C4[Business Class]
        C4 --> C5[Retention]
        C5 --> C6[Access Class]
    end
    subgraph Compliance
        D1[GDPR] --> D2[HIPAA]
        D2 --> D3[SOX]
        D3 --> D4[PCI]
        D4 --> D5[Standards]
        D5 --> D6[Custom]
    end
    subgraph Protect
        E1[Encryption] --> E2[Access Ctrl]
        E2 --> E3[Masking]
        E3 --> E4[Tokenization]
        E4 --> E5[DLP]
        E5 --> E6[Audit Log]
    end
    subgraph Rights
        F1[Access] --> F2[Rectify]
        F2 --> F3[Erase]
        F3 --> F4[Portability]
        F4 --> F5[Object]
        F5 --> F6[Consent]
    end
    subgraph PrivacyOps
        G1[PIA] --> G2[DPA]
        G2 --> G3[Vendor Mgmt]
        G3 --> G4[IR]
        G4 --> G5[Training]
        G5 --> G6[Reporting]
    end
    subgraph AutoInt
        H1[Workflow Auto] --> H2[API Int]
        H2 --> H3[DB Int]
        H3 --> H4[Cloud Int]
        H4 --> H5[ID Int]
        H5 --> H6[Sec Int]
    end
    subgraph Monitor
        I1[Metrics] --> I2[Compliance]
        I2 --> I3[Risk]
        I3 --> I4[Incident]
        I4 --> I5[Audit]
        I5 --> I6[Exec Report]
    end
    A6 --> B1
    B6 --> C1
    C6 --> D1
    D6 --> E1
    E6 --> F1
    F6 --> G1
    G6 --> H1
    H6 --> I1
    %% Feedback Loops
    I1 --> C1
    I2 --> D1
    I3 --> E1
    I4 --> F1
    I5 --> G1
    I6 --> H1
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
    A[DSAR Received] --> B[DSAR Portal]
    B -->|Trigger| C[Auto Search]
    C -->|Results| D[Review]
    D -->|Fulfill| E[Data Subject]
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
    A[Policy Def] --> B[Policy Engine]
    B -->|Enforce| C[Data Access]
    C -->|Monitor| D[Audit Logs]
    D -->|Alert| E[Privacy Team]
```
**Tools:** Open Policy Agent, Apache Ranger, DataSunrise, Elastic Security

**Automation/AI Tips:**
- Automate policy enforcement and real-time monitoring
- Use LLMs to analyze audit logs for privacy violations

**Metrics:** 100% policy coverage, reduced privacy incidents

**References:** Open Policy Agent, Apache Ranger, DataSunrise 