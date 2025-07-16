# Security Awareness & Training Architectures

---

## 1. Security Awareness Training Portal

**Description:**
Delivers security training modules, quizzes, and tracks user progress to improve organizational security culture.

**Architecture Diagram:**
```mermaid
flowchart TD
    A[Admin] -->|Create Module| B[Training Platform]
    B -->|Assign| C[User]
    C -->|Complete Module| B
    B -->|Progress/Results| D[Reporting Dashboard]
    D -->|Export| E[Management/Compliance]
```

**Key Components:**
- Training Platform: Delivers modules, tracks progress (e.g., [Open Source Security Awareness Platform](https://github.com/toniblyx/security-tools/blob/master/README.md#security-awareness-training)).
- Reporting Dashboard: Visualizes completion, risk, and trends.
- Management/Compliance: Consumes reports for oversight and audits.
- User: Employees or test users.

---

## 2. Phishing Simulation Platform

**Description:**
Sends simulated phishing emails to users, tracks responses, and provides metrics for awareness training and risk assessment.

**Architecture Diagram:**
```mermaid
flowchart TD
    A[Admin/Security Team] -->|Create Campaign| B[Phishing Platform]
    B -->|Send Emails| C[User Targets]
    C -->|Clicks/Responses| B
    B -->|Metrics/Reports| D[Dashboard]
    D -->|Awareness Training| C
```

**Key Components:**
- Phishing Platform: Manages campaigns, templates, and delivery (e.g., [GoPhish](https://getgophish.com/)).
- User Targets: Employees or test users.
- Dashboard: Visualizes metrics, click rates, and risk.
- Awareness Training: Delivers follow-up training to users who fall for simulations. 