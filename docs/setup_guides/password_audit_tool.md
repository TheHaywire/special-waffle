# Setup Guide: Open-Source Password Audit & Breach Checker Tool

---

## Overview
This guide explains how to deploy and use an open-source password audit and breach checker tool, such as Pwned Passwords, open-source audit scripts, or a custom checker. These tools help identify weak, reused, or breached passwords in your environment.

---

## Prerequisites
- Linux server, VM, or desktop (Ubuntu recommended)
- Python 3.x
- Docker (optional, for containerized deployment)
- List of password hashes or plaintext passwords (for audit)

---

## Step 1: Choose Your Tool
- **Pwned Passwords**: Use the [Have I Been Pwned API](https://haveibeenpwned.com/API/v3#PwnedPasswords) or download the offline hash set
- **Open-Source Audit Scripts**: Use tools like [pwdlyser](https://github.com/bitcrackcyber/pwdlyser), [CrackMapExec](https://github.com/Porchetta-Industries/CrackMapExec), or custom Python scripts
- **Custom Checker**: Build your own with Python and the HIBP API

---

## Step 2: Audit Passwords with Pwned Passwords (API Example)
```python
import requests
import hashlib

def check_pwned(password):
    sha1 = hashlib.sha1(password.encode('utf-8')).hexdigest().upper()
    prefix, suffix = sha1[:5], sha1[5:]
    url = f'https://api.pwnedpasswords.com/range/{prefix}'
    res = requests.get(url)
    hashes = (line.split(':') for line in res.text.splitlines())
    return any(suffix == h for h, _ in hashes)

print(check_pwned('password123'))  # True if breached
```

---

## Step 3: Offline Audit (Optional)
- Download the [Pwned Passwords hash set](https://haveibeenpwned.com/Passwords)
- Use tools like pwdlyser or custom scripts to check hashes locally

---

## Step 4: Integrate with User Directory
- Export password hashes from Active Directory, LDAP, or local files (ensure compliance and privacy)
- Run the audit tool against the exported hashes
- Report weak, reused, or breached passwords to users/admins

---

## Step 5: Enforce Remediation
- Require password changes for users with weak or breached passwords
- Educate users on strong password practices

---

## Troubleshooting Tips
- Respect privacy and legal requirements when handling passwords
- For large datasets, use offline checking to avoid API rate limits
- Hash all passwords before checking (never send plaintext to external APIs)
- Regularly update breach data sets for accuracy

---

## References
- [Have I Been Pwned API](https://haveibeenpwned.com/API/v3#PwnedPasswords)
- [pwdlyser GitHub](https://github.com/bitcrackcyber/pwdlyser)
- [CrackMapExec GitHub](https://github.com/Porchetta-Industries/CrackMapExec) 