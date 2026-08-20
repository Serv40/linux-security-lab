## Project 01 - Baseline Enumeration

This document records the commands used during the initial baseline assessment.

## 1. System Identity

```bash
hostname
cat /etc/os-release
uname -a
```
Purpose: Identify the hostname operating system, version, kernel, and architecture.

# 2. User Identity

```bash
whoami
id
groups
```
Purpose: Identify the current user, UID/GID, and group memberships

# 3. Network Enumeration

```bash
ip addr
ip route
```
Purpose: Identify network interfaces, IP addresses, subnet information, and routing.

# 4. Listening Ports

```bash
ss -tulpn
```
Purpose: Identify listening network ports and their associated services.

# 5. Running Services

```bash
systemctl --type=service --state=running
```
Purpose: Identify currently running system services.

# 6. Process Enumeration

```bash
ps aux --sort=-rss | head -15
```
Purpose: Identify processes using the most resident memory.

# 7. Filesystem

```bash
df -h
ls -lah /
ls -lah /home/debian
ls -lah /var/www/html
```
Purpose: Inspect filesystem usage and baseline file permissiions.

# 8. Memory

```bash
free -h
```
Purpose: Record RAM and Swap usage.

# 9. Service Status

```bash
systemctl status apache2 --no-pager
systemctl status ssh --no-pager
```
Purpose: Verify the current state of Apache and SSH.

# 10. SSH Logs

Root access was remporarily obtained using:
```bash
su -
````
SSH service logs were then inspected with:
```bash
journalctl -u ssh --since "1 hour ago" --no-pager
```
Purpose: Inspect SSH service events recorded by systemd-journald

# 11. Authentication Log Check

```bash
tail -n 30 /var/log/auth.log
```
Result:
/var/log/auth.log does not exist.
(SSH events were available through `systemd-journald`

