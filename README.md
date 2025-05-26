# 🔍 Network Security Scan Report

![Cybersecurity Banner](https://via.placeholder.com/800x200.png?text=Network+Security+Scan)

## 📌 Executive Summary
This report documents a network reconnaissance exercise performed on a local subnet (`10.0.2.0/24`) using **Nmap** for port scanning and **Wireshark** for packet analysis.

### Key Findings
- Discovered **X active hosts** on the network
- Identified **Y open ports** running services (SSH, HTTP, etc.)
- Detected potential vulnerabilities (e.g., outdated services)

## 🛠️ Tools Used
| Tool | Version | Purpose |
|------|---------|---------|
| [Nmap](https://nmap.org) | 7.80 | Port scanning and service detection |
| [Wireshark](https://www.wireshark.org) | 3.6.5 | Packet capture and analysis |

## 🔧 Methodology

### Nmap Scanning
```bash
# SYN Scan (Stealth Scan)
sudo nmap -sS 10.0.2.0/24 -oN syn_scan.txt

# Service Version Detection
sudo nmap -sV 10.0.2.0/24 -oN service_versions.txt

# Aggressive Scan
sudo nmap -A 10.0.2.0/24 -oN aggressive_scan.txt
