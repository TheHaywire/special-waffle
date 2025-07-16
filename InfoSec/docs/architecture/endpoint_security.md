# Endpoint Security Architectures

---

## 1. Open Source EDR (Endpoint Detection & Response)

**Description:**
An open source EDR agent monitors endpoints for suspicious activity, collects telemetry, and enables detection, investigation, and response to threats.

**Architecture Diagram:**
```mermaid
flowchart TD
    A[Endpoint Device] -->|Telemetry| B[EDR Agent]
    B -->|Events| C[Central EDR Server]
    C -->|Detection/Analysis| D[Security Analyst]
    C -->|Response Actions| A
    C -->|Logs| E[SIEM/Log Management]
```

**Key Components:**
- Endpoint Device: Workstation, server, or laptop.
- EDR Agent: Collects process, file, and network activity.
- Central EDR Server: Aggregates events, runs detection logic, and orchestrates response.
- Security Analyst: Investigates alerts and initiates response.
- SIEM/Log Management: Stores events for correlation and compliance.

---

## 2. Automated Malware Analysis Sandbox

**Description:**
A sandbox environment automatically analyzes suspicious files or URLs by executing them in isolation and observing their behavior.

**Architecture Diagram:**
```mermaid
flowchart TD
    A[User/Analyst] -->|Submit File/URL| B[Sandbox UI/API]
    B -->|Sample| C[Sandbox Environment]
    C -->|Behavioral Data| D[Analysis Engine]
    D -->|Report| E[User/Analyst]
    D -->|Logs| F[SIEM/Log Management]
```

**Key Components:**
- Sandbox UI/API: Interface for submitting samples and viewing results.
- Sandbox Environment: Isolated VM or container for safe execution.
- Analysis Engine: Monitors system changes, network activity, and indicators of compromise.
- User/Analyst: Reviews reports and takes action.
- SIEM/Log Management: Stores analysis logs and results. 