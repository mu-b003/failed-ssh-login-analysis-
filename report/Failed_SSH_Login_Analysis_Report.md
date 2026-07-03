# Failed SSH Login Analysis Report

## Executive Summary

This project demonstrates the analysis of failed SSH authentication attempts on an Ubuntu system. A controlled lab environment was created using Kali Linux as the attacker machine and Ubuntu as the target server. Failed login attempts were intentionally generated through manual SSH connections and an automated password guessing tool. The authentication logs were then analyzed to identify attack patterns, source IP addresses, targeted accounts, and evidence of brute-force activity.

---

# Objective

The objective of this project was to:

* Analyze failed SSH authentication attempts.
* Identify the source IP address of the attack.
* Determine which user accounts were targeted.
* Detect brute-force behavior using Linux authentication logs.
* Document the findings and provide security recommendations.

---

# Lab Environment

| Component        | Description       |
| ---------------- | ----------------- |
| Attacker Machine | Kali Linux        |
| Target Machine   | Ubuntu Linux      |
| Service          | OpenSSH Server    |
| Protocol         | SSH               |
| Port             | 22                |
| Log File         | /var/log/auth.log |

---

# Attack Scenario

The OpenSSH server was installed and configured on the Ubuntu machine.

Several local user accounts were created for testing purposes:

* developer
* IT-support
* asmin

Authentication failures were generated in two ways:

1. Manual SSH login attempts using incorrect passwords.
2. Automated password guessing using Hydra against the SSH service.

The purpose of these activities was to generate realistic authentication logs for forensic analysis.

---

# Log Collection

Authentication events were collected from:

/var/log/auth.log

The following Linux utilities were used during the investigation:

* grep
* awk
* sort
* uniq
* head
* tail

These commands were used to filter authentication failures, identify source IP addresses, count repeated events, and determine targeted accounts.

---

# Analysis

The authentication logs revealed multiple failed SSH login attempts originating from a single IP address.

The failed login attempts targeted several user accounts, including valid users and an invalid username.

The following usernames were observed:

* developer
* IT-support
* admin (invalid user)

Multiple authentication failures occurred within a very short period, especially during the automated Hydra attack, indicating brute-force behavior.

---

# Findings

## Source IP

192.168.150.128

## Targeted Accounts

* developer
* IT-support
* admin (invalid user)

## Failed Login Attempts

| Username   | Attempts |
| ---------- | -------: |
| admin      |       13 |
| developer  |        3 |
| IT-support |        3 |

## Source IP Summary

| Source IP       | Failed Attempts |
| --------------- | --------------: |
| 192.168.150.128 |              19 |

## Attack Characteristics

* Multiple failed SSH login attempts.
* Repeated authentication failures from a single source.
* Attempts against both valid and invalid usernames.
* Automated password guessing activity.
* No successful authentication observed during the attack.

---

# Indicators of Compromise (IoCs)

| Indicator        | Value                               |
| ---------------- | ----------------------------------- |
| Source IP        | 192.168.150.128                     |
| Target Service   | SSH                                 |
| Destination Port | 22                                  |
| Attack Type      | Failed Authentication / Brute Force |
| Invalid Username | admin                               |

---

# Security Impact

The investigation indicates that the SSH service was targeted by repeated authentication attempts.

Although no successful login occurred, the observed activity demonstrates the typical behavior of a brute-force attack against an SSH service.

If left unmonitored, similar attacks could eventually compromise weak user credentials.

---

# Recommendations

* Enable Fail2Ban to automatically block repeated failed login attempts.
* Enforce strong password policies.
* Disable password authentication when possible and use SSH public key authentication.
* Restrict SSH access using firewall rules.
* Monitor authentication logs regularly.
* Limit remote administrative access to trusted hosts.
* Enable account lockout policies where appropriate.

---

# Conclusion

The investigation successfully identified repeated failed SSH authentication attempts targeting the Ubuntu server.

Analysis of the authentication logs showed that all observed failures originated from a single source IP address and targeted multiple user accounts. The frequency and timing of the authentication failures are consistent with brute-force attack behavior.

No successful login attempts were identified during the investigation, indicating that the attack was unsuccessful. Continuous monitoring of authentication logs and implementation of defensive controls such as strong password policies and automated blocking mechanisms are recommended to reduce the risk of future attacks.

---

# Skills Demonstrated

* Linux Administration
* SSH Authentication Analysis
* Authentication Log Analysis
* Linux Log Investigation
* Brute Force Detection
* Bash Log Parsing
* Incident Documentation
* Blue Team Fundamentals
* SOC Analyst Workflow
