# Setup Guide: Open-Source Security Awareness Training Portal

---

## Overview
This guide explains how to deploy an open-source security awareness training portal using Moodle, a custom LMS, or an open-source quiz platform. The portal will deliver training modules, quizzes, and track user progress to improve organizational security culture.

---

## Prerequisites
- Linux server or VM (Ubuntu recommended)
- 2+ GB RAM, 2+ CPUs
- Docker (recommended) or root access for manual install
- Domain name and SSL certificate (recommended for production)
- SMTP server credentials (for user notifications)

---

## Step 1: Choose Your Platform
- **Moodle**: Popular open-source LMS ([moodle.org](https://moodle.org/))
- **Custom LMS**: Build with Python (Django), Node.js, or PHP
- **Quiz Platform**: Use open-source quiz tools (e.g., [Quizzer](https://github.com/quizzer/quizzer))

---

## Step 2: Quick Start with Docker (Moodle Example)
```bash
docker run -d -p 8080:80 --name moodle moodlehq/moodle-php-apache:latest
```
- Access Moodle at http://localhost:8080
- Complete the web-based setup (DB, admin user, SMTP)

---

## Step 3: Manual Install (Alternative)
- Download Moodle from [moodle.org](https://download.moodle.org/)
- Follow [Moodle install docs](https://docs.moodle.org/400/en/Installation_quick_guide)

---

## Step 4: Create Training Content
- Add courses for topics like phishing, password hygiene, social engineering, etc.
- Use built-in quiz and assignment modules
- Upload videos, PDFs, and interactive content

---

## Step 5: Enroll Users and Track Progress
- Add users manually, via CSV, or enable self-registration
- Assign courses and monitor completion rates
- Set up email notifications and reminders

---

## Troubleshooting Tips
- Ensure required ports (80/443/8080) are open
- For email, configure SMTP settings in the admin panel
- Check logs for errors if the site does not load or emails fail
- Regularly update the platform for security patches

---

## References
- [Moodle Docs](https://docs.moodle.org/)
- [Quizzer GitHub](https://github.com/quizzer/quizzer) 