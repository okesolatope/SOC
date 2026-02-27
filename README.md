# Operation AgroDefend – SOC in a Segmented Network

##  Project Overview

Operation AgroDefend is a hands-on Security Operations Center (SOC) simulation project designed to demonstrate enterprise-grade threat detection, network segmentation, and centralized log monitoring within a controlled lab environment.

This project replicates a real-world business scenario for an agricultural technology company requiring improved visibility, attack detection, and incident response across segmented network zones.

---

##  Lab Architecture

The environment was built using the following technologies:

- **pfSense** – Firewall & network segmentation
- **Wazuh (SIEM)** – Log collection, correlation & alerting
- **Ubuntu Server** – DMZ victim server
- **Windows 10** – Monitored endpoint
- **Kali Linux** – Attack simulation machine

### Network Segmentation

The infrastructure was divided into three logical segments:

| Segment | Purpose | IP Address |
|----------|----------|------------|
| WAN | External simulation network | 10.0.2.15 |
| LAN | Internal corporate network | 192.168.2.5 |
| DMZ | Public-facing services | 192.168.3.5 |

Firewall rules were configured to restrict lateral movement between LAN and DMZ segments.

---

##  SOC Deployment

### Wazuh Implementation

- Wazuh Manager deployed in LAN segment
- Agents installed on:
  - Windows 10 (LAN)
  - Ubuntu Server (DMZ)
- Centralized log forwarding enabled
- Dashboard used for real-time monitoring and alert analysis

---

##  Reconnaissance & Attack Simulation

### Network Discovery

- `nmap -sn` – Host discovery
- `nmap -sS` – TCP SYN scan
- `nmap -sU` – UDP scan

### Attack Scenarios

1. **SSH Brute-Force Attack**
   - Target: Ubuntu DMZ Server
   - Username targeted: `admin`
   - Tool: Hydra (via Kali Linux)

2. **FTP Brute-Force Attack**
   - Target: Ubuntu DMZ Server
   - Tool: Hydra

All attacks were conducted in a controlled lab environment for defensive security analysis.

---

##  Detection & Findings

Wazuh successfully detected:

- Multiple failed login attempts
- Repeated brute-force attempts against the `admin` account
- Source IP generating malicious traffic
- High-severity authentication alerts
- Correlated firewall and endpoint logs

Segmentation controls successfully prevented lateral movement into the LAN environment.

---

##  MITRE ATT&CK Mapping

- **T1110 – Brute Force**
- Potential risk of **Valid Accounts abuse** if credentials were compromised

---

##  Security Recommendations

- Enforce strong password policies
- Implement account lockout after **4 failed login attempts**
- Restrict SSH access between network segments
- Enable Multi-Factor Authentication (MFA)
- Improve firewall logging and monitoring
- Implement continuous SOC monitoring and alert tuning

---

##  Skills Demonstrated

- Network segmentation design
- Firewall configuration (pfSense)
- SIEM deployment and management (Wazuh)
- Log correlation and threat analysis
- Incident investigation
- SOC reporting and documentation
- Risk assessment and mitigation planning

---

##  Project Objective

This project demonstrates how combining network segmentation, firewall enforcement, and centralized SIEM monitoring significantly improves enterprise threat visibility and incident response readiness.

Operation AgroDefend showcases practical SOC implementation skills aligned with real-world defensive security operations.

---

##  Deliverables

- Network diagram
- Firewall rule configuration
- Wazuh dashboard alerts
- Log evidence from endpoints
- Professional SOC report
- Executive summary presentation

---

##  Conclusion

Operation AgroDefend validates the effectiveness of segmentation, centralized logging, and structured SOC processes in detecting and mitigating brute-force attacks within an enterprise network.

This project reflects real-world defensive security practices and SOC operational readiness.
