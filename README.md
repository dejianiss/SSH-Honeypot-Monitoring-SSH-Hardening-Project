# 🛡️ SSH Honeypot Monitoring & SSH Hardening Project

<p align="center">
  <img src="https://shields.io" />
  <img src="https://shields.io" />
  <img src="https://shields.io" />
</p>

---

## 👤 Project Owner

**Ayodeji Gabriel Anigboro**

---

## 🎯 Objective

The SSH Honeypot Monitoring Project was designed to simulate real-world Security Operations Center (SOC) activities involving SSH attack detection, log analysis, system hardening, and threat mitigation on a Linux server.

The project focuses on monitoring SSH authentication attempts, identifying brute-force attacks through log analysis, hardening SSH configurations to reduce attack exposure, and blocking malicious IP addresses using firewall rules.

This project demonstrates practical blue-team security skills commonly performed by SOC Analysts and System Administrators.

---

## 🧠 Skills Learned

* Linux authentication log analysis
* SSH security monitoring
* Brute-force attack detection
* Linux system hardening
* Firewall rule implementation
* IP reputation and attack source identification
* Security event investigation
* Incident response fundamentals
* Linux command-line operations
* SOC Tier 1 monitoring workflows

---

## 🛠️ Tools Used

<p align="left">

<img src="https://shields.io" />
<img src="https://shields.io" />
<img src="https://shields.io" />
<img src="https://shields.io" />
<img src="https://shields.io" />
<img src="https://shields.io" />
<img src="https://shields.io" />

</p>

---

## 🏗️ Architecture Flow

Attacker System (Metasploit VM)
↓
SSH Login Attempts
↓
Target Linux System
↓
/var/log/auth.log
↓
Log Analysis & IP Extraction
↓
SSH Hardening Controls
↓
iptables Firewall Rules
↓
Attacker IP Blocked

---

## Steps

<p><strong>Ref 1: SSH Service Status Verification</strong><br>
This screenshot shows the OpenSSH service running successfully on the Linux target system. Verifying service availability ensures the SSH server is ready to receive authentication requests and generate security logs for monitoring purposes.</p>

<img src="INSERT_SCREENSHOT_1.png" width="700" alt="SSH Service Running">

<p>SSH Service Running Successfully</p><br>

---

<p><strong>Ref 2: SSH Authentication Log Monitoring</strong><br>
This screenshot displays real-time monitoring of the Linux authentication log using the auth.log file. Failed SSH login attempts are captured and recorded by the operating system, providing valuable forensic data for security investigations.</p>

<img src="live_auth_monitoring.png" width="700" alt="Auth Log Monitoring">

<p>Live SSH Authentication Logging</p><br>

---

<p><strong>Ref 3: Simulated SSH Brute-Force Attempts</strong><br>
This screenshot demonstrates repeated failed login attempts from an external system against the SSH service. The activity simulates a brute-force attack commonly observed by SOC analysts in production environments.</p>

<img src="brute_force_auth_failures.png" width="700" alt="Failed SSH Logins">

<p>Simulated SSH Attack Activity</p><br>

---

<p><strong>Ref 4: SSH Hardening Configuration</strong><br>
This screenshot shows security enhancements applied within the SSH daemon configuration file. Controls such as disabling root login, limiting authentication attempts, reducing login timeout periods, and restricting user access significantly reduce the server's attack surface.</p>

<img src="ssh_hardening_config.png" width="700" alt="SSH Hardening">

<p>SSH Security Configuration Changes</p><br>

---

<p><strong>Ref 5: SSH Service Restart After Hardening</strong><br>
This screenshot confirms successful restart of the SSH service after applying security configuration changes. Restarting the service activates the new defensive controls.</p>

<img src="ssh_service_restart.png" width="700" alt="SSH Restart">

<p>SSH Service Restart Confirmation</p><br>

---

<p><strong>Ref 6: Failed Login Extraction from Authentication Logs</strong><br>
This screenshot demonstrates extraction of failed SSH authentication events from auth.log. The command filters security-relevant events to support investigation and threat hunting activities.</p>

<img src="failed_login_extraction.png" width="700" alt="Failed Password Extraction">

<p>Failed Login Event Analysis</p><br>

---

<p><strong>Ref 7: Attacker IP Frequency Analysis</strong><br>
This screenshot shows the identification of attacker IP addresses through log parsing and aggregation. Repeated login attempts from the same source indicate potential brute-force activity requiring mitigation.</p>

<img src="iptables_mitigation_and_verification.png" width="700" alt="Attacker IP Analysis">

<p>Attacker IP Detection Results</p><br>

---

<p><strong>Ref 8: Firewall Rule Creation Using iptables</strong><br>
This screenshot demonstrates implementation of a firewall rule designed to block a malicious IP address identified during the investigation. This action represents the containment phase of the incident response process.</p>

<img src="iptables_mitigation_and_verification.png" width="700" alt="iptables Blocking Rule">

<p>Firewall-Based Threat Mitigation</p><br>

---

<p><strong>Ref 9: Verification of Active Firewall Rules</strong><br>
This screenshot confirms that the firewall rule has been successfully applied and is actively protecting the SSH service from further access attempts originating from the identified attacker IP address.</p>

<img src="iptables_mitigation_verification.png" width="700" alt="iptables Verification">

<p>Blocked Attacker Verification</p><br>

---

## 🔍 Security Analysis

During testing, multiple failed SSH authentication attempts were generated against the target Linux system. Authentication logs were continuously monitored using auth.log and analysed using command-line tools to identify suspicious activity.

Repeated login failures originating from the same source IP address were classified as brute-force behaviour. SSH hardening controls were then implemented to reduce exposure to password-guessing attacks.

Following investigation, malicious source IPs were blocked using iptables firewall rules, effectively preventing further unauthorized authentication attempts.

---

## 🚨 Detection Logic

### Failed SSH Authentication Detection

```bash
grep "Failed password" /var/log/auth.log
```

### Attacker IP Enumeration

```bash
grep "Failed password" /var/log/auth.log | awk '{print \$(NF-3)}' | sort | uniq -c
```

### Block Malicious IP

```bash
sudo iptables -A INPUT -s <attacker-ip> -j DROP
```

---

## 🛡️ Mitigation Measures Implemented

* Disabled SSH root login
* Reduced maximum authentication attempts
* Reduced login grace timeout
* Restricted authorized users
* Monitored authentication logs
* Identified attacker IP addresses
* Applied firewall-based IP blocking
* Saved firewall persistence rules

---

## 📈 Project Outcomes

* Successfully monitored SSH authentication activity
* Simulated brute-force attack behaviour
* Identified malicious source IP addresses
* Implemented SSH hardening controls
* Applied active network-level threat mitigation
* Demonstrated SOC-style detection and response workflow

---

## 🎓 SOC Analyst Relevance

This project demonstrates practical experience in:

* Linux log monitoring
* Threat detection
* Incident investigation
* SSH security management
* Firewall administration
* Brute-force attack analysis
* Defensive security operations
* SOC Tier 1 responsibilities

These are core skills frequently required for Cybersecurity Analysts and entry-level SOC roles.
