# MITRE ATT&CK Mapping — BOTS v2 Investigation

## Compromised Host
**MERCURY**  
Domain: **FROTHLY**

---

## Phase 1 — Initial Reconnaissance  
**Technique:** T1046 — Network Service Discovery  

**Description:**  
The attacker enumerated active network services and listening ports on the compromised host to understand available attack surfaces.

**Evidence:**  
- netstat execution identifying listening ports

---

## Phase 2 — Brute Force Authentication  
**Technique:** T1110 — Brute Force  

**Description:**  
Multiple abnormal authentication attempts were observed against privileged accounts, indicating password guessing activity prior to access.

**Evidence:**  
- repeated failed authentication attempts  
- abnormal login patterns targeting privileged accounts  

---

## Phase 3 — Privileged Logon  
**Technique:** T1078 — Valid Accounts  

**Description:**  
The attacker successfully obtained and used valid privileged credentials to execute commands on MERCURY.

**Evidence:**  
- successful privileged execution context  
- administrative process creation events  

---

## Phase 4 — Remote Execution (WinRM)  
**Technique:** T1021.006 — Windows Remote Management  

**Description:**  
The attacker executed commands remotely on MERCURY via Windows Remote Management, evidenced by repeated WinRM host processes.

**Evidence:**  
- repeated `wsmprovhost.exe` executions  
- remote PowerShell session activity  

---

## Phase 5 — Defense Evasion & Persistence  
**Techniques:**  
- T1059.001 — PowerShell  
- T1562 — Impair Defenses  
- T1053 — Scheduled Task  

**Description:**  
The attacker deployed obfuscated PowerShell payloads with AMSI bypass and modified scheduled tasks and registry entries to evade detection and maintain persistence.

**Evidence:**  
- obfuscated PowerShell payload  
- AMSI bypass execution  
- scheduled task deletion  
- registry modifications  

---

## Phase 6 — Discovery  
**Techniques:**  
- T1082 — System Information Discovery  
- T1016 — Network Discovery  

**Description:**  
The attacker performed host and network enumeration to understand system context and connectivity.

**Evidence:**  
- whoami execution  
- netstat enumeration  

---

## Phase 7 — Exfiltration  
**Technique:** T1048 — Exfiltration Over Alternative Protocol  

**Description:**  
Data was exfiltrated from MERCURY using FTP via scripted command execution.

**Evidence:**  
- `ftp.exe -s` scripted transfer  
- outbound data transfer activity  

---

## Summary

The attack chain on MERCURY demonstrates a complete post-compromise intrusion lifecycle including credential abuse, remote execution, persistence establishment, internal discovery, and data exfiltration.  
All observed behaviors align with known MITRE ATT&CK techniques commonly associated with Windows domain intrusions.

---

**Analyst:** Dimitrios Anastasiou  
**Dataset:** Splunk BOTS v2  
**Case:** MERCURY Host Compromise  
