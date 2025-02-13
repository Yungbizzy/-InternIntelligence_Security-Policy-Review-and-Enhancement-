# -InternIntelligence_Security-Policy-Review-and-Enhancement-
# Security Policy Review And Enhancement Report

## Executive Summary
This report provides a comprehensive assessment of the organization’s security policies, identifies key gaps, and recommends enhancements aligned with industry standards such as **ISO/IEC 27001** and the **NIST Cybersecurity Framework (CSF)**. Additionally, it includes a structured **Linux security implementation guide** to strengthen policy enforcement and improve overall cybersecurity resilience.

---

## Security Policy Assessment Findings

| s/n | Policy | Gaps Identified | Recommendations |
|----|----------------------|-------------------------------|--------------------------------------------------|
| 1 | Access Control Policy | No MFA, weak password policies, no role-based access | Enforce MFA, RBAC, least privilege, and session timeouts |
| 2 | Data Protection Policy | No clear data classification and weak encryption | Enforce AES-256 encryption, classify data, and secure disposal |
| 3 | Incident Response Plan | No structured response and no automated detection | Implement SIEM, define response playbooks, and conduct drills |
| 4 | Network Security Policy | Lack of segmentation, no IDS/IPS and weak VPN policies | Use VLAN segmentation, deploy IDS/IPS, and enforce VPN security |
| 5 | Risk Management Policy | No regular security assessments, weak vendor controls | Conduct bi-annual risk assessments, enforce third-party compliance |

---

## Enhanced Security Policies

### 1. Access Control Policy
**Purpose:** Ensure only authorized personnel access company resources. 
![image](https://github.com/user-attachments/assets/df0a5230-302f-4431-9a0d-9e0c27b500bd)

**Key Enhancements:**
- MFA required for all critical systems.
- RBAC (Role-Based Access Control) implemented for least privilege access.
- Session timeout: 15 minutes of inactivity leads to automatic logout.
- Quarterly access reviews to remove unnecessary permissions.

### 2. Data Protection Policy
**Purpose:** Protect sensitive company and customer data from unauthorized access.  
**Key Enhancements:**
- AES-256 encryption for sensitive data storage.
- Data Classification: Categorized as Public, Internal, Confidential, Restricted.
- Secure disposal: Use `shred` command and degaussing for data deletion.
- 5-year data retention policy unless regulatory compliance dictates otherwise.

### 3. Incident Response Plan
**Purpose:** Define a structured response to security incidents.  
**Key Enhancements:**
- Incident categorization: Low, Medium, High, Critical.
- All incidents reported within 30 minutes.
- Containment & Recovery: Immediate isolation of affected systems.
- Post-Incident Review: Lessons learned documented within 7 days.

### 4. Network Security Policy
**Purpose:** Secure network infrastructure and prevent cyber threats.
![image](https://github.com/user-attachments/assets/6ec911ca-281a-4de9-9450-f782ed7279ee)

**Key Enhancements:**
- Firewalls & IDS/IPS: Mandatory at all network perimeters.
- Network segmentation: VLANs to isolate sensitive systems.
- Mandatory VPN usage for remote employees.
- Traffic monitoring: **Zeek, Suricata** for real-time analysis.

### 5. Risk Management Policy
**Purpose:** Identify, assess, and mitigate cybersecurity risks.
![image](https://github.com/user-attachments/assets/0e4aa17d-7182-4139-9c4e-b794c5d5204e)

**Key Enhancements:**
- Risk assessments **bi-annually** using **ISO 27005** framework.
- Threat modeling aligned with **MITRE ATT&CK** framework.
- Vendor risk assessment mandatory for all third-party integrations.

---

## Linux Security Implementation Guide

### 1. Access Control & Authentication
#### Enable Multi-Factor Authentication (MFA)
```bash
sudo apt install libpam-google-authenticator  # Installs MFA package
google-authenticator  # Generates a QR code for MFA setup
```

#### Restrict Root Access
```bash
sudo nano /etc/ssh/sshd_config  # Edit SSH configuration
PermitRootLogin no  # Disable root login
sudo systemctl restart ssh  # Restart SSH service
```

#### Password Hardening
```bash
sudo nano /etc/security/pwquality.conf  # Configure password policies
minlen = 12  # Set minimum password length
minclass = 3  # Require at least three character classes
```

#### Full-Disk Encryption with LUKS
```bash
sudo apt install cryptsetup  # Installs encryption tool
sudo cryptsetup luksFormat /dev/sdX  # Encrypts disk partition
```

---

### 2. Incident Response and Monitoring
#### Install SIEM (Wazuh/ELK Stack) for Real-Time Monitoring
- Wazuh provides centralized logging, event correlation, and threat detection.

#### Deploy OSSEC for Host Intrusion Detection
```bash
sudo apt install ossec-hids  # Installs OSSEC for intrusion detection
sudo systemctl start ossec  # Starts OSSEC monitoring service
```

#### Use Fail2Ban to Block Brute-Force Attacks
```bash
sudo apt install fail2ban  # Installs Fail2Ban
sudo systemctl start fail2ban  # Starts the Fail2Ban service
```

---

### 3. Network Security & Hardening
#### Enable UFW Firewall
```bash
sudo apt install ufw  # Installs UFW
sudo ufw enable  # Enables firewall
sudo ufw allow ssh  # Allows SSH connections
```

#### Monitor Traffic with Zeek
```bash
sudo apt install zeek  # Installs Zeek
sudo zeekctl start  # Starts Zeek monitoring
```

---

## Recommendations
- **Review & Approve Policies** – Ensure all stakeholders understand and approve updates.
- **Enforce Security Controls** – Implement Linux security configurations as outlined.
- **Conduct Awareness Training** – Educate employees on access control & incident reporting.
- **Continuous Monitoring & Compliance** – Schedule quarterly security audits and annual penetration tests.

---

## Conclusion
This report outlines critical security policy gaps and provides a structured approach to enhancing security posture. By implementing the recommended policies and security tools, the organization will strengthen its defenses against cyber threats, improve incident response capabilities, and ensure regulatory compliance. Continuous monitoring and periodic reviews are essential for maintaining security resilience.

---
