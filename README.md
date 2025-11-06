# Secure_Lab_Lite
Learnbay Task1

## Overview
Tiny security lab with one Ubuntu Server and one Windows VM and one kali-Linux. Performed basic hardening and simple network discovery using Nmap.

## VMs & IPs
- Ubuntu Server 22.04 — 10.22.14.64 (before restart)   |  10.116.247.64 (after restart)
- Windows 10 — 10.22.14.143 (before restart)           |  10.116.247.143 (after restart)
- Kali — 10.116.247.159

## Tools used
- VMware Workstation
- Nmap
- OpenSSH (Ubuntu)
- PowerShell (Windows)
- OBS (for demo recording)

## Steps to reproduce
1. Boot the VMs and ensure network Custom: Specific Virtual Network(VMnet0).
2. On Ubuntu:
   - `sudo adduser student_ubuntu`
   - `sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config && sudo systemctl restart sshd`
   - capture `ls -l /etc/ssh/sshd_config` and `grep PermitRootLogin /etc/ssh/sshd_config`
3. On Windows (Admin PowerShell):
   - `net user student Password@123 /add`
   - `Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -Name "fDenyTSConnections" -Value 1`
   - `Set-NetFirewallRule -DisplayGroup "Remote Desktop" -Enabled False`
4. Nmap scans:
   - Quick_ubuntu: `nmap -Pn -O -p- -sV --min-rate=100 10.22.14.64 -oN student_ubuntu.txt`
   - Quick_windows: `nmap -Pn -O -p- -sV --min-rate=100 10.22.14.143 -oN student_windows.txt`

## Deliverables
- `screenshots`
- `report.md` (1–2 pages)
- `demo.mp4` (5-minute recording)
