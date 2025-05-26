# 🔍 Network Security Scan Report

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
```
## 📊 Results

### 🔍 Nmap Scan Results

| IP Address | Open Ports | Services       | Notes                          |
|------------|------------|----------------|--------------------------------|
| 10.0.2.1   | 22, 80, 443| SSH, HTTP, HTTPS| Potential router admin portal  |
| 10.0.2.5   | 445        | SMB            | **Warning**: SMBv1 detected ([CVE-2017-0143](https://nvd.nist.gov/vuln/detail/CVE-2017-0143)) |

📌 **Key Observations**:
- Router admin interface accessible at `10.0.2.1:80`
- Outdated SMB protocol version detected (critical vulnerability)

### 📡 Wireshark Packet Analysis

**Total packets captured**: 1,200+

**Traffic Analysis**:
```plaintext
Source            Destination       Protocol  Info
10.0.2.15         10.0.2.1         TCP       SYN → Port 22 [Scan]
10.0.2.1          10.0.2.15        TCP       SYN/ACK ← Port 22 [Open]
10.0.2.15         10.0.2.5         TCP       SYN → Port 445 [Scan]
10.0.2.5          10.0.2.15        TCP       RST ← Port 445 [Filtered]
