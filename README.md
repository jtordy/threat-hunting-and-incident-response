<h1>Threat Hunting and Incident Response</h1>

<h2>Description</h2> This project demonstrates a structured approach to threat hunting and incident response using both hands-on host/network scanning and threat intelligence-driven analysis. The workflow includes:

- Network reconnaissance and vulnerability scanning

- Service enumeration and CVE analysis

- MITRE ATT&CK-based threat hunting

- Business impact assessment and reporting

It highlights real-world techniques, detection playbooks, and recommendations for securing critical systems against emerging adversary behaviors.

 <h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>

- <b>Nmap</b>

- <b>Wireshark</b>

- <b>Windows Event Viewer</b>

- <b>MITRE ATT&CK Framework</b>

<h2>Environments Used</h2>

- <b>Windows Server 2019</b>

- <b>Windows 10 Pro (21H2)</b>

- <b>Ubuntu Linux</b>

<h2>Program Walk-through:</h2> <p align="center"> Network scan of <b>scanme.nmap.org</b>: <br/> <img src="screenshots/nmap_scanme_version.png" width="80%" alt="Nmap Scan"/> <br /><br /> Network scan of <b>testphp.vulnweb.com</b>: <br/> <img src="screenshots/nmap_testphp_syn.png" width="80%" alt="Nmap Scan"/> <br /><br /> Vulnerability identified: <b>CVE-2014-0226</b> on Apache 2.4.7<br/> <img src="screenshots/cve_analysis.png" width="80%" alt="CVE Analysis"/> <br /><br /> MITRE-driven threat hunting: mapping observed techniques<br/> <img src="screenshots/mitre_playbook.png" width="80%" alt="MITRE Playbook"/> </p>
<h2>Key Findings</h2>

- Network Recon & Enumeration

  - <b>scanme.nmap.org</b> open ports: 22, 53, 80, 2000, 5060, 9929, 31337

  - <b>testphp.vulnweb.com</b> open ports: 53, 80, 443, 2000, 5060

- Vulnerabilities

  - CVE-2014-0226 on Apache 2.4.7 (Medium, CVSS 6.4–6.8)

  - Potential denial-of-service, info disclosure, or remote code execution

- <b> MITRE Observed Techniques (Case Studies) </b>

| Case                       | Techniques                                                                                                                        | Source                  |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| CrowdStrike 2025           | T1059 (PowerShell/command scripts), T1218 (Signed binary proxy/LOLBins), T1078 (Valid Accounts), T1530/T1567 (Cloud exfiltration) | CrowdStrike 2025 Report |
| CISA SimpleHelp RMM/Medusa | T1190 (Exploit public-facing app), T1566 (Phishing), T1486 (Ransomware encryption)                                                | CISA Advisory           |
| Scattered Spider           | T1566 (Phishing), T1078/T1136 (Account misuse), T1087 (Account discovery), T1567 (Cloud exfiltration)                             | CISA/FBI 2025 Update    |


- Aggregated Trends

  - Malware-free/living-off-the-land intrusions increasing

  - Credential theft and account takeover recurring in ransomware/APT campaigns

  - RMM & external-facing service vulnerabilities remain primary access vectors

  - Cloud exfiltration rising; should be treated as a primary target

<h2>Projected Techniques (Next 6–12 Months)</h2>

T1098 – Account manipulation/persistence

T1136 – Account creation (local/cloud)

T1567.002 – Exfiltration to cloud storage (S3/MEGA/Dropbox)

T1548 – Abuse elevation control mechanisms (privilege escalation)

T1090/T1105 – App-layer C2 and remote services

<h2>Detection & Hunt Playbook</h2>

Detect PowerShell encoded commands: -EncodedCommand / Invoke-Expression

Monitor new cloud/service account creation and suspicious OAuth consents (Azure AuditLogs)

Track connections/uploads to consumer cloud storage (s3.amazonaws.com, mega.nz, dropbox.com)

Identify repeated MFA push requests followed by success (MFA fatigue / push-bombing)

<h2>Recommendations & Defensive Priorities</h2>

Patch all external-facing vulnerabilities immediately (focus on RMM/Exchange)

Enforce phishing-resistant MFA and reduce push-approval workflows

Treat cloud accounts as first-class assets: enable logging, conditional access, monitor service principals

Harden RMM access and monitor for remote admin anomalies

Add detections for living-off-the-land behaviors (LOLBins, PowerShell encoded commands)

<h2>Skills Demonstrated</h2>

Network reconnaissance and threat hunting

Vulnerability identification and CVE analysis

MITRE ATT&CK-based detection and playbook creation

Incident documentation and business impact assessment

SOC-style reporting and mitigation recommendations
