# Setup Guide: Self-Healing Infrastructure Demo

---

## Overview
This guide demonstrates how to build a self-healing infrastructure using open-source tools such as Open Policy Agent (OPA), Cloud Custodian, and Ansible or AWS Lambda for automated remediation. The example focuses on cloud resources (e.g., AWS S3 buckets), but the approach is adaptable to other environments.

---

## Prerequisites
- Cloud account (e.g., AWS)
- Python 3.x
- Docker (for OPA testing)
- AWS CLI configured (if using AWS)
- Permissions to create and modify cloud resources

---

## Step 1: Define Policy-as-Code
Use OPA or Cloud Custodian to define security and compliance policies. Example: Ensure all S3 buckets are not public.

### Example: Cloud Custodian Policy (YAML)
```yaml
policies:
  - name: s3-no-public-buckets
    resource: s3
    filters:
      - type: value
        key: PublicAccessBlockConfiguration.RestrictPublicBuckets
        value: false
    actions:
      - type: set-public-block
        state: true
```
Save as `custodian-s3-policy.yml`.

---

## Step 2: Deploy Policy Engine
Run Cloud Custodian as a scheduled job (locally, in CI, or as a Lambda function):

```bash
pip install c7n
custodian run -s output custodian-s3-policy.yml
```

Or, for OPA, write a Rego policy and use OPA as a sidecar or admission controller (for Kubernetes/IaC).

---

## Step 3: Automate Remediation
For more complex remediation, use Ansible or AWS Lambda. Example: Auto-remediate non-compliant S3 buckets.

### Example: Ansible Playbook
```yaml
- hosts: localhost
  connection: local
  tasks:
    - name: Block public access on all S3 buckets
      amazon.aws.s3_bucket:
        name: "{{ item }}"
        public_access_block:
          block_public_acls: true
          block_public_policy: true
          ignore_public_acls: true
          restrict_public_buckets: true
      loop: "{{ query('aws_s3_bucket_facts').buckets | map(attribute='name') | list }}"
```

Or, use AWS Lambda triggered by CloudWatch Events to remediate in real time.

---

## Step 4: Monitor & Alert
- Integrate with CloudWatch, SIEM, or email for alerting on policy violations and remediation actions.
- Store logs for audit and compliance.

---

## Troubleshooting Tips
- Ensure IAM permissions allow policy enforcement and remediation actions.
- Test policies in dry-run mode before enabling auto-remediation.
- Review logs for failed actions or permission errors.
- For OPA, use the Playground (https://play.openpolicyagent.org/) to test Rego policies.

---

## References
- [Cloud Custodian Docs](https://cloudcustodian.io/docs/)
- [OPA Docs](https://www.openpolicyagent.org/docs/)
- [Ansible AWS Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_aws.html)
- [AWS Lambda Docs](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) 