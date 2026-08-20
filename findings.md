## Project 01 - Baseline Security Assessment

## Assessment Status

Current stage:
BEFORE HARDENING

No intentional security hardening changes have been performed yet.

## System Identity

- Hostname: ranudeb
- Debian Version: 13.6
- Kernel: 6.12.101+deb13-amd64
- Architecture: x86_64
- Current User: debian
- UID: 1000

## Network

- Interface: enp1s0
- IPv4: 192.168.122.252/24
- Gateway: 192.168.122.1

## Listening Services

Two primary listening TCP services were identified.
Port	Protocol	Service			Purpose
22	TCP		OpenSSH	 		Remote administration
80	TCP		Apache HTTP Server	Web server

SSH was observed listening on:
0.0.0.0:22
[::]:22
Apache was observed as an active HTTP service.

## Running Services

The following services were observed during the baseline:
- apache2.service
- cron.service
- dbus.service
- getty@tty1.service
- ssh.service
- systemd-journald.service
- systemd-logind.service
- systemd-timesyncd.service
- systemd-udevd.service
- user@1000.service
The presence of a running service is not automatically considered a security vulnerability.
Further assessment is required to determine which services are necessary.

## Apache Baseline

Apache was observed as:
- active (running)
- enabled

Document root:
- /var/www/html

Current web file:
- /var/www/html/index.html

Permissions:
- -rw-r--r-- root root index.html

Further Apache security assessment is pending.

## SSH Baseline

OpenSSH was observed as:
- active (running)
- enabled

The SSH daemon was listening on:
- 0.0.0.0:22
- [::]:22
SSH service logs were available through systemd-journald.

The SSH startup log confirmed:
- Server listening on 0.0.0.0 port 22.
- Server listening on :: port 22.
- Started ssh.service - OpenBSD Secure Shell server.
Detailed SSH configuration assessment is pending.

## Logging Baseline

The system uses systemd-journald for system logging.

The file below was not present:
- /var/log/auth.log

SSH service events were successfully retrieved through:
```bash
journalctl -u ssh
```
When journalctl was executed as the debian user, the system indicated that messages from other users
and the system were not fully visible.

Root access was required to inspect the full SSH service journal.

# Resource Baseline

	Memory
Resource 	Value
Total RAM	~1.9 GiB
Used 		~268 MiB
Available	~1.7 GiB
Swap		~1.1 GiB
Swap Used	~0 B

	Disk
Resource	Value
Device		/dev/vda1
Total		19 GiB
Used		~1.3 GiB
Available	~17 GiB
Usage  		~7 %		

The server currently has relatively low resource utilization.

# Initial Security Observations

The baseline assessment identified the following areas for further investigation:
- SSH is enabled and exposed on TCP port 22.
- Apache is enabled and exposed on TCP port 80.
- SSH is listening on all IPv4 and IPv6 interfaces.
- The current user is a non-root account.
- sudo is not installed.
- System logging is handled through systemd-journald.
- The web root is owner by root.
- The system uses a minimal installation without a desktop environment.
These observations are baseline conditions, not confirmed vulnerabilities.

# Pending Assessment
- User and group privileges.
- Root account configuration.
- sudo configuration.
- File and directory permissions.
- SSH configuration.
- Password authentication.
- Root login configuration.
- Firewall status.
- Installed packages.
- Apache configuration.
- Apache security settings.
- Logging and monitoring configuration.

# Before vs After

This section will be completed after the hardening stage.
Security Area 			Before		After
User Privileges			Pending		Pending
SSH Configuration		Pending		Pending
Root Login 			Pending		Pending
Password Authentication		Pending		Pending
Firewall			Pending		Pending
File Permissions		Pending		Pending
Apache Configuration		Pending		Pending
Logging 			Pending		Pending
