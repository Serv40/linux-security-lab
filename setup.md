# Setup

## Project 01 - Debian LInux Server Security Lab

## 1. Virtual Machine
This security lab is running inside a virtual machine.

The guest operating system uses a minimal Debian Netints installation without a desktop environment.

## 2. Operating System
- OS: Debian GNU/Linux 13 (trixie)
- Debian version: 13.6
- Architecture: x86_64
- Kernel: 6.12.101+deb13-amd64
- Desktop Environment: None

## 3. Services

The server currently provides two primary services.

### OpenSSH

Used for remote administration and SSH security testing.

- Service: `ssh.service`
- Port: TCP/22

### Apache HTTP Server

Used as the web server for the lab.

- Service `apache2.service`
- POrt: TCP/80
- Document root: `/var/www/html`

## 4. Host Information

- Hostname: ranudeb
- Current User: debian
- UID: 1000

## 5. Network

- Network interface: enp1s0
- IPv4 address: `192.168.122.252/24`
- Default gateway: `192.168.122.1`

## 6. VM Resources

Baseline recources observed during assessment:

- RAM: ~1.9 GiB
- Swap: ~1.1 GiB
- Disk: 19 GiB

The VM intentionally uses a minimal installation without a desktop environment.
