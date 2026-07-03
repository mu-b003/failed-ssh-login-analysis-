# Commands Used

This document lists the Linux commands used during the SSH failed login analysis.

---

## 1. Update Package Repository

```bash
sudo apt update
```

Updates the package index before installing software.

---

## 2. Install OpenSSH Server

```bash
sudo apt install openssh-server
```

Installs the OpenSSH server on the Ubuntu target machine.

---

## 3. Verify SSH Service Status

```bash
sudo systemctl status ssh
```

Checks the current status of the SSH service.

---

## 4. Monitor Authentication Logs

```bash
sudo tail -f /var/log/auth.log
```

Displays authentication log entries in real time.

---

## 5. Create Test User Accounts

```bash
sudo adduser developer
```

```bash
sudo adduser IT-support
```

```bash
sudo adduser asmin
```

Creates user accounts for authentication testing.

---

## 6. Manual SSH Login Attempt (Kali Linux)

```bash
ssh developer@192.168.150.129
```

Attempts to log in to the Ubuntu SSH server.

---

## 7. Create Password List

```bash
touch passwords.txt
```

Creates a password wordlist file.

---

## 8. Edit Password List

```bash
nano passwords.txt
```

Adds passwords to the wordlist.

---

## 9. Generate Failed Login Attempts

```bash
hydra -l admin -P passwords.txt ssh://192.168.150.129
```

Performs password guessing against the SSH service in the lab environment.

---

## 10. Display Failed Login Events

```bash
sudo grep "Failed password" /var/log/auth.log
```

Displays all failed SSH authentication events.

---

## 11. Count Failed Attempts by Source IP

```bash
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr
```

Counts failed authentication attempts by source IP address.

---

## 12. Count Failed Attempts by Username

```bash
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-5)}' | sort | uniq -c | sort -nr
```

Summarizes failed authentication attempts by username.

---

## 13. Count Total Failed Authentication Events

```bash
sudo grep -c "Failed password" /var/log/auth.log
```

Counts all log entries containing failed password events.

---

## 14. Display the First Failed Authentication Event

```bash
sudo grep "Failed password" /var/log/auth.log | head -1
```

Displays the earliest failed authentication event.

---

## 15. Display the Last Failed Authentication Event

```bash
sudo grep "Failed password" /var/log/auth.log | tail -1
```

Displays the last matching authentication event.
