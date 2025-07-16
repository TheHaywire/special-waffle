# Setup Guide: Secure DevSecOps CI/CD Pipeline

---

## Overview
This guide walks you through setting up a secure CI/CD pipeline with integrated security checks (SAST, DAST, dependency scanning, IaC scanning, SBOM) using open-source tools. The example uses GitHub Actions, but the concepts apply to GitLab CI, Jenkins, etc.

---

## Prerequisites
- Source code repository (e.g., GitHub)
- Docker (for running scanners)
- Access to GitHub Actions or similar CI/CD platform

---

## Step 1: Repository Structure
Organize your repo with the following structure:
```
/ (root)
  |-- .github/workflows/ci.yml
  |-- src/
  |-- infrastructure/
  |-- requirements.txt / package.json / pom.xml (as applicable)
```

---

## Step 2: Example GitHub Actions Workflow
Below is a sample `ci.yml` integrating SAST (Semgrep), DAST (OWASP ZAP), dependency scanning (Trivy), IaC scanning (Checkov), and SBOM generation (Syft):

```yaml
name: Secure CI/CD Pipeline
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build-and-scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Python (if needed)
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'

      - name: Install dependencies
        run: |
          pip install -r requirements.txt || true

      - name: SAST with Semgrep
        uses: returntocorp/semgrep-action@v1
        with:
          config: 'auto'

      - name: Dependency Scan with Trivy
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: 'fs'
          scan-ref: '.'

      - name: IaC Scan with Checkov
        uses: bridgecrewio/checkov-action@v12
        with:
          directory: ./infrastructure

      - name: Generate SBOM with Syft
        uses: anchore/sbom-action@v0
        with:
          path: '.'
          format: 'cyclonedx-json'

      - name: DAST with OWASP ZAP (optional, for web apps)
        run: |
          docker run -t owasp/zap2docker-stable zap-baseline.py -t http://localhost:8000 -r zap_report.html || true

      - name: Upload reports
        uses: actions/upload-artifact@v3
        with:
          name: security-reports
          path: |
            zap_report.html
            semgrep.sarif
            trivy-results.sarif
            checkov.sarif
            sbom.cyclonedx.json
```

---

## Step 3: Review & Enforce Pipeline Gates
- Configure the pipeline to fail on high/critical findings (adjust as needed for your risk tolerance).
- Use GitHub branch protection rules to require passing security checks before merging.

---

## Step 4: Monitor & Store Results
- Integrate with SIEM/log management for long-term storage and alerting.
- Use GitHub Security tab or upload SARIF reports for visualization.

---

## Troubleshooting Tips
- Ensure all required tools are available in the CI environment (use Docker if needed).
- For private dependencies, configure authentication/secrets in CI.
- Some scanners may produce false positives—review findings before blocking deploys.
- For DAST, ensure the target app is running and accessible from the CI runner.

---

## References
- [Semgrep Docs](https://semgrep.dev/docs/)
- [OWASP ZAP Docs](https://www.zaproxy.org/docs/)
- [Trivy Docs](https://aquasecurity.github.io/trivy/)
- [Checkov Docs](https://www.checkov.io/1.Welcome.html)
- [Syft Docs](https://github.com/anchore/syft) 