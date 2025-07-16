# Pro Workflows: Critical Infrastructure Security

## 1. ICS/SCADA Network Segmentation & Monitoring
**Problem:** Flat networks in critical infrastructure increase the risk of widespread compromise.

**Workflow:**
```mermaid
flowchart TD
    %% Critical Infrastructure Sectors
    subgraph "Critical Infrastructure Sectors"
        A1[Energy - Power Plants/Grid/Utilities]
        A2[Transportation - Airports/Railways/Highways]
        A3[Water - Treatment Plants/Distribution Systems]
        A4[Manufacturing - Industrial Plants/Assembly Lines]
        A5[Healthcare - Hospitals/Medical Devices]
        A6[Communications - Telecom/Internet/Data Centers]
    end
    
    %% ICS/SCADA Systems
    subgraph "ICS/SCADA Systems"
        B1[Supervisory Control - HMI/SCADA Servers]
        B2[Programmable Logic Controllers - PLCs/RTUs]
        B3[Distributed Control Systems - DCS/Field Devices]
        B4[Safety Instrumented Systems - SIS/ESD Systems]
        B5[Industrial Networks - Fieldbus/Modbus/Ethernet]
        B6[Legacy Systems - Older/Unsupported Equipment]
    end
    
    %% Network Architecture & Segmentation
    subgraph "Network Architecture & Segmentation"
        C1[Enterprise Network - Business/IT Systems]
        C2[DMZ Network - Internet-facing Services]
        C3[Control Network - SCADA/HMI Systems]
        C4[Field Network - PLCs/RTUs/Field Devices]
        C5[Safety Network - SIS/ESD/Critical Safety]
        C6[Isolation Zones - Air-gapped/Secure Enclaves]
    end
    
    %% Security Controls & Monitoring
    subgraph "Security Controls & Monitoring"
        D1[Firewalls - Next-gen/Industrial/Application]
        D2[Intrusion Detection - IDS/IPS/Network Monitoring]
        D3[Access Control - Authentication/Authorization]
        D4[Data Protection - Encryption/Backup/Recovery]
        D5[Physical Security - Access Control/Surveillance]
        D6[Environmental Monitoring - Temperature/Humidity/Power]
    end
    
    %% Threat Detection & Response
    subgraph "Threat Detection & Response"
        E1[Anomaly Detection - ML/AI/Behavioral Analysis]
        E2[Threat Intelligence - ICS-specific/Industry Feeds]
        E3[Incident Response - ICS-specific Playbooks]
        E4[Forensic Analysis - Digital/Physical Evidence]
        E5[Recovery Planning - Business Continuity/Disaster Recovery]
        E6[Communication - Internal/External/Regulatory]
    end
    
    %% Compliance & Standards
    subgraph "Compliance & Standards"
        F1[NERC CIP - Electric Grid Security]
        F2[NIST Cybersecurity Framework - Risk Management]
        F3[ISA/IEC 62443 - Industrial Security Standards]
        F4[ISO 27001 - Information Security Management]
        F5[Industry-specific Standards - Sector Requirements]
        F6[Regulatory Requirements - Government/State Laws]
    end
    
    %% Asset Management & Inventory
    subgraph "Asset Management & Inventory"
        G1[Asset Discovery - Automated/Manual Inventory]
        G2[Vulnerability Assessment - Scanning/Testing]
        G3[Configuration Management - Baselines/Standards]
        G4[Patch Management - Security/Functional Updates]
        G5[Lifecycle Management - Procurement/Retirement]
        G6[Risk Assessment - Asset/System/Network Risk]
    end
    
    %% Operational Technology Security
    subgraph "Operational Technology Security"
        H1[Device Security - Hardening/Configuration]
        H2[Protocol Security - Modbus/DNP3/Ethernet Security]
        H3[Application Security - HMI/SCADA Application Security]
        H4[Data Security - Historian/Archive/Backup Security]
        H5[Communication Security - Network/Protocol Encryption]
        H6[Physical Security - Facility/Equipment Protection]
    end
    
    %% Business Continuity & Resilience
    subgraph "Business Continuity & Resilience"
        I1[Disaster Recovery - Backup/Restore/Recovery]
        I2[Business Continuity - Critical Operations/Processes]
        I3[Redundancy - Systems/Networks/Power]
        I4[Failover - Automatic/Manual System Switching]
        I5[Testing - DR/BC/Incident Response Testing]
        I6[Documentation - Procedures/Plans/Processes]
    end
    
    %% Integration & Automation
    subgraph "Integration & Automation"
        J1[Security Tool Integration - SIEM/EDR/DLP]
        J2[OT System Integration - SCADA/HMI/PLC APIs]
        J3[Business System Integration - ERP/MES/CRM]
        J4[Monitoring Integration - APM/Logging/Alerting]
        J5[Compliance Integration - GRC/Policy Management]
        J6[Third-party Integration - Vendors/Partners/Services]
    end
    
    %% Data Flow Connections
    A1 --> B1
    A2 --> B1
    A3 --> B1
    A4 --> B2
    A5 --> B2
    A6 --> B2
    
    B1 --> C1
    B2 --> C1
    B3 --> C1
    B4 --> C2
    B5 --> C2
    B6 --> C2
    
    C1 --> D1
    C2 --> D1
    C3 --> D1
    C4 --> D2
    D5 --> D2
    D6 --> D2
    
    D1 --> E1
    D2 --> E1
    D3 --> E1
    D4 --> E2
    E5 --> E2
    E6 --> E2
    
    E1 --> F1
    E2 --> F1
    E3 --> F1
    E4 --> F2
    F5 --> F2
    F6 --> F2
    
    F1 --> G1
    F2 --> G1
    F3 --> G1
    F4 --> G2
    G5 --> G2
    G6 --> G2
    
    G1 --> H1
    G2 --> H1
    G3 --> H1
    G4 --> H2
    H5 --> H2
    H6 --> H2
    
    H1 --> I1
    H2 --> I1
    H3 --> I1
    H4 --> I2
    I5 --> I2
    I6 --> I2
    
    I1 --> J1
    I2 --> J1
    I3 --> J1
    I4 --> J2
    J5 --> J2
    J6 --> J2
    
    %% Feedback Loops
    J1 --> B1
    J2 --> C1
    J3 --> D1
    J4 --> E1
    J5 --> F1
    J6 --> G1
```
**Tools:** Snort, Suricata, pfSense, custom segmentation scripts

**Automation/AI Tips:**
- Automate network segmentation policy enforcement
- Use LLMs to analyze IDS/IPS alerts for critical threats

**Metrics:** 100% network segmentation, reduced lateral movement

**References:** Snort, Suricata, ICS security best practices

---

## 2. OT Asset Inventory & Vulnerability Management
**Problem:** Untracked OT assets and unpatched vulnerabilities are a major risk in critical infrastructure.

**Workflow:**
```mermaid
flowchart TD
    %% OT Asset Categories
    subgraph "OT Asset Categories"
        A1[Control Systems - SCADA/DCS/PLC/RTU]
        A2[Network Infrastructure - Switches/Routers/Firewalls]
        A3[End Devices - Sensors/Actuators/Valves/Pumps]
        A4[Safety Systems - SIS/ESD/Safety Instrumented Systems]
        A5[Legacy Systems - Older/Unsupported/Proprietary Equipment]
        A6[Support Systems - Historian/Engineering/Administrative]
    end
    
    %% Asset Discovery & Inventory
    subgraph "Asset Discovery & Inventory"
        B1[Network Discovery - Active/Passive/Agent-based Scanning]
        B2[Device Identification - Manufacturer/Model/Version/Firmware]
        B3[Asset Classification - Critical/Important/Standard/Non-critical]
        B4[Location Tracking - Physical/Logical/Network Location]
        B5[Relationship Mapping - Dependencies/Connections/Data Flow]
        B6[Documentation - Manual/Automated/Updated Asset Records]
    end
    
    %% Vulnerability Assessment
    subgraph "Vulnerability Assessment"
        C1[Automated Scanning - OpenVAS/Nessus/Qualys/ICS-specific]
        C2[Manual Assessment - Penetration Testing/Security Review]
        C3[Configuration Review - Security Settings/Baselines/Standards]
        C4[Firmware Analysis - Version/Update Status/Security Patches]
        C5[Protocol Analysis - Modbus/DNP3/Ethernet/IP Security]
        C6[Physical Security - Access Control/Environmental/Safety]
    end
    
    %% Risk Assessment & Prioritization
    subgraph "Risk Assessment & Prioritization"
        D1[Criticality Assessment - Safety/Operations/Business Impact]
        D2[Vulnerability Scoring - CVSS/ICS-specific/Environmental Factors]
        D3[Threat Assessment - Attack Vectors/Adversary Capabilities]
        D4[Exploitability Analysis - Complexity/Prerequisites/Resources]
        D5[Impact Analysis - Safety/Operations/Financial/Reputational]
        D6[Risk Prioritization - Critical/High/Medium/Low Risk Ranking]
    end
    
    %% Remediation Planning & Execution
    subgraph "Remediation Planning & Execution"
        E1[Patch Management - Security/Functional/Compatibility Testing]
        E2[Configuration Hardening - Security Settings/Baselines/Standards]
        E3[Network Segmentation - VLANs/Firewalls/Access Control]
        E4[Compensating Controls - Monitoring/Detection/Response]
        E5[Vendor Coordination - Manufacturer/Support/Update Coordination]
        E6[Change Management - Approval/Testing/Deployment/Validation]
    end
    
    %% Monitoring & Validation
    subgraph "Monitoring & Validation"
        F1[Continuous Monitoring - Asset Status/Performance/Security]
        F2[Vulnerability Tracking - Open/Closed/In-progress Issues]
        F3[Compliance Monitoring - Regulatory/Industry/Internal Standards]
        F4[Performance Monitoring - System/Network/Application Performance]
        F5[Security Monitoring - Threats/Incidents/Anomalies]
        F6[Validation Testing - Remediation/Effectiveness/Regression Testing]
    end
    
    %% Compliance & Standards
    subgraph "Compliance & Standards"
        G1[NERC CIP - Electric Grid Security Requirements]
        G2[ISA/IEC 62443 - Industrial Security Standards]
        G3[NIST Cybersecurity Framework - Risk Management]
        G4[Industry-specific Standards - Sector Requirements]
        G5[Internal Policies - Security/Operations/Maintenance]
        G6[Audit Requirements - Internal/External/Regulatory]
    end
    
    %% Integration & Automation
    subgraph "Integration & Automation"
        H1[Asset Management Integration - CMDB/ITAM/OTAM Systems]
        H2[Security Tool Integration - SIEM/EDR/Vulnerability Management]
        H3[Business System Integration - ERP/MES/CRM Systems]
        H4[Monitoring Integration - APM/Logging/Alerting Platforms]
        H5[Compliance Integration - GRC/Policy Management Tools]
        H6[Third-party Integration - Vendors/Partners/Services]
    end
    
    %% Reporting & Analytics
    subgraph "Reporting & Analytics"
        I1[Asset Reports - Inventory/Status/Compliance Reports]
        I2[Vulnerability Reports - Assessment/Remediation/Status Reports]
        I3[Risk Reports - Assessment/Mitigation/Trend Analysis]
        I4[Compliance Reports - Audit/Assessment/Status Reports]
        I5[Executive Reports - KPIs/Metrics/ROI Analysis]
        I6[Stakeholder Reports - Board/Regulators/Customers]
    end
    
    %% Data Flow Connections
    A1 --> B1
    A2 --> B1
    A3 --> B1
    A4 --> B2
    A5 --> B2
    A6 --> B2
    
    B1 --> C1
    B2 --> C1
    B3 --> C1
    B4 --> C2
    C5 --> C2
    C6 --> C2
    
    C1 --> D1
    C2 --> D1
    C3 --> D1
    C4 --> D2
    D5 --> D2
    D6 --> D2
    
    D1 --> E1
    D2 --> E1
    D3 --> E1
    D4 --> E2
    E5 --> E2
    E6 --> E2
    
    E1 --> F1
    E2 --> F1
    E3 --> F1
    E4 --> F2
    F5 --> F2
    F6 --> F2
    
    F1 --> G1
    F2 --> G1
    F3 --> G1
    F4 --> G2
    G5 --> G2
    G6 --> G2
    
    G1 --> H1
    G2 --> H1
    G3 --> H1
    G4 --> H2
    H5 --> H2
    H6 --> H2
    
    H1 --> I1
    H2 --> I1
    H3 --> I1
    H4 --> I2
    I5 --> I2
    I6 --> I2
    
    %% Feedback Loops
    I1 --> B1
    I2 --> C1
    I3 --> D1
    I4 --> E1
    I5 --> F1
    I6 --> G1
```
**Tools:** Nmap, OpenVAS, custom asset scripts

**Automation/AI Tips:**
- Automate asset discovery and vulnerability scanning
- Use LLMs to prioritize remediation based on risk

**Metrics:** 95%+ asset coverage, reduced unpatched vulnerabilities

**References:** Nmap, OpenVAS, ICS-CERT

---

## 3. Incident Response Automation for Critical Infrastructure
**Problem:** Manual incident response is too slow for high-impact critical infrastructure attacks.

**Workflow:**
```mermaid
flowchart TD
    %% Incident Detection & Alerting
    subgraph "Incident Detection & Alerting"
        A1[Security Monitoring - SIEM/EDR/Threat Detection]
        A2[Anomaly Detection - ML/AI/Behavioral Analysis]
        A3[Threat Intelligence - IOCs/TTPs/Indicators]
        A4[Vulnerability Alerts - Scanner/Assessment/Exploit Alerts]
        A5[Operational Alerts - System/Network/Performance Issues]
        A6[External Alerts - ICS-CERT/Vendor/Partner Notifications]
    end
    
    %% SOAR Platform & Orchestration
    subgraph "SOAR Platform & Orchestration"
        B1[Incident Triage - Automated/Manual/Expert Review]
        B2[Playbook Execution - Automated/Manual/Approval-based]
        B3[Tool Orchestration - Security/IT/OT Tool Integration]
        B4[Workflow Automation - Process/Approval/Notification]
        B5[Case Management - Investigation/Tracking/Documentation]
        B6[Collaboration - Team/Stakeholder/External Coordination]
    end
    
    %% Automated Response Actions
    subgraph "Automated Response Actions"
        C1[Network Isolation - Segment/Block/Quarantine Actions]
        C2[Access Control - Account/Privilege/Session Management]
        C3[System Hardening - Configuration/Security/Policy Updates]
        C4[Data Protection - Backup/Encryption/Recovery Actions]
        C5[Communication - Internal/External/Regulatory Notifications]
        C6[Monitoring Enhancement - Additional/Enhanced/Continuous Monitoring]
    end
    
    %% Critical Infrastructure Specific Response
    subgraph "Critical Infrastructure Specific Response"
        D1[Safety System Response - SIS/ESD/Safety Protocol Activation]
        D2[Operational Continuity - Critical Operations/Process Protection]
        D3[Regulatory Notification - NERC/EPA/DHS/State Agencies]
        D4[Public Communication - Press/Stakeholders/Customer Notifications]
        D5[Law Enforcement Coordination - FBI/CISA/State/Local Authorities]
        D6[Industry Coordination - ISACs/Partners/Vendors/Suppliers]
    end
    
    %% Investigation & Forensics
    subgraph "Investigation & Forensics"
        E1[Digital Forensics - System/Network/Application Analysis]
        E2[Physical Forensics - Facility/Equipment/Environmental Analysis]
        E3[Evidence Collection - Digital/Physical/Testimonial Evidence]
        E4[Timeline Analysis - Event/Activity/Communication Timeline]
        E5[Root Cause Analysis - Technical/Process/People Factors]
        E6[Attribution Analysis - Actor/Motivation/Capability Assessment]
    end
    
    %% Recovery & Restoration
    subgraph "Recovery & Restoration"
        F1[System Recovery - Backup/Restore/Recovery Procedures]
        F2[Network Recovery - Connectivity/Communication/Data Flow]
        F3[Operational Recovery - Process/Production/Service Restoration]
        F4[Data Recovery - Backup/Archive/Data Integrity Validation]
        F5[Security Recovery - Controls/Monitoring/Protection Restoration]
        F6[Business Continuity - Critical Functions/Alternative Operations]
    end
    
    %% Lessons Learned & Improvement
    subgraph "Lessons Learned & Improvement"
        G1[Incident Analysis - What Happened/Why/How to Prevent]
        G2[Process Improvement - Response/Recovery/Prevention Processes]
        G3[Technology Improvement - Tools/Systems/Infrastructure Updates]
        G4[Training Improvement - Staff/Skill/Knowledge Enhancement]
        G5[Policy Improvement - Security/Operational/Compliance Policies]
        G6[Testing Improvement - Incident Response/Recovery/Prevention Testing]
    end
    
    %% Compliance & Reporting
    subgraph "Compliance & Reporting"
        H1[Regulatory Reporting - NERC/EPA/DHS/State Requirements]
        H2[Industry Reporting - ISACs/Partners/Stakeholder Reports]
        H3[Internal Reporting - Executive/Board/Management Reports]
        H4[Audit Documentation - Evidence/Procedures/Compliance Records]
        H5[Performance Metrics - Response Time/Recovery Time/Effectiveness]
        H6[Continuous Improvement - Process/Technology/People Optimization]
    end
    
    %% Integration & Automation
    subgraph "Integration & Automation"
        I1[Security Tool Integration - SIEM/EDR/Threat Intel Platforms]
        I2[IT System Integration - Network/System/Application Management]
        I3[OT System Integration - SCADA/HMI/PLC/Control Systems]
        I4[Business System Integration - ERP/MES/CRM/Operations Systems]
        I5[Communication Integration - Email/SMS/Phone/Video Systems]
        I6[Third-party Integration - Vendors/Partners/Services]
    end
    
    %% Data Flow Connections
    A1 --> B1
    A2 --> B1
    A3 --> B1
    A4 --> B2
    A5 --> B2
    A6 --> B2
    
    B1 --> C1
    B2 --> C1
    B3 --> C1
    B4 --> C2
    C5 --> C2
    C6 --> C2
    
    C1 --> D1
    C2 --> D1
    C3 --> D1
    C4 --> D2
    D5 --> D2
    D6 --> D2
    
    D1 --> E1
    D2 --> E1
    D3 --> E1
    D4 --> E2
    E5 --> E2
    E6 --> E2
    
    E1 --> F1
    E2 --> F1
    E3 --> F1
    E4 --> F2
    F5 --> F2
    F6 --> F2
    
    F1 --> G1
    F2 --> G1
    F3 --> G1
    F4 --> G2
    G5 --> G2
    G6 --> G2
    
    G1 --> H1
    G2 --> H1
    G3 --> H1
    G4 --> H2
    H5 --> H2
    H6 --> H2
    
    H1 --> I1
    H2 --> I1
    H3 --> I1
    H4 --> I2
    I5 --> I2
    I6 --> I2
    
    %% Feedback Loops
    I1 --> B1
    I2 --> C1
    I3 --> D1
    I4 --> E1
    I5 --> F1
    I6 --> G1
```
**Tools:** Shuffle, TheHive, custom SOAR scripts

**Automation/AI Tips:**
- Automate incident response playbooks for common attack scenarios
- Use LLMs to generate incident summaries and lessons learned

**Metrics:** 90%+ incident containment rate, reduced response time

**References:** Shuffle, TheHive, ICS-CERT 