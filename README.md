# Failed SSH Login Analysis

## Overview

This project demonstrates the investigation of failed SSH authentication attempts on an Ubuntu server. A controlled lab environment was created using Kali Linux as the attacker and Ubuntu as the target system. Authentication logs were analyzed to identify failed login attempts, attacker IP addresses, targeted user accounts, and indicators of brute-force activity.

---

## Objectives

* Analyze SSH authentication logs.
* Detect failed login attempts.
* Identify attacker IP addresses.
* Identify targeted user accounts.
* Detect brute-force behavior.
* Document the investigation process.

---

## Lab Environment

| Component      | Details             |
| -------------- | ------------------- |
| Attacker       | Kali Linux          |
| Target         | Ubuntu Linux        |
| Service        | OpenSSH Server      |
| Protocol       | SSH                 |
| Port           | 22                  |
| Log Source     | `/var/log/auth.log` |
| Virtualization | VMware Workstation  |

---

## Project Structure

```text
Failed-SSH-Login-Analysis/
│
├── README.md
|--DISCLAIMER.md
├── report/
├── evidence/
├── screenshots/
├── commands/
└── LICENSE
```

---

## Investigation Workflow

1. Configure the SSH service.
2. Create test user accounts.
3. Generate failed SSH login attempts.
4. Collect authentication logs.
5. Analyze failed login events.
6. Extract source IP addresses.
7. Identify targeted usernames.
8. Document findings.

---

## Key Findings

* Multiple failed SSH login attempts were detected.
* All attack attempts originated from a single source IP.
* Both valid and invalid user accounts were targeted.
* Authentication failures matched brute-force attack behavior.
* No successful login was observed.

---

## Skills Demonstrated

* Linux Administration
* SSH Security
* Authentication Log Analysis
* Bash Log Parsing
* Incident Investigation
* Brute Force Detection
* Blue Team Fundamentals
* SOC Analysis

---

## Tools Used

* Ubuntu
* Kali Linux
* OpenSSH
* VMware Workstation
* Hydra
* grep
* awk
* sort
* uniq

---

## Report

The complete investigation report is available in the `report/` directory.

---

## Screenshots

Screenshots demonstrating the attack simulation and investigation process are available in the `screenshots/` directory.

---

## Disclaimer

This project was performed in a controlled laboratory environment for educational and defensive cybersecurity purposes only.
