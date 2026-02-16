# Case Overview — MERCURY Host Compromise (BOTS v2)

## Scenario Summary

This investigation analyzes a Windows domain compromise using the Splunk BOTS v2 dataset.  
The focus of the analysis is host **MERCURY**, which shows clear evidence of attacker activity including remote execution, persistence mechanisms, and data exfiltration.

The objective of this case study is to reconstruct the attacker’s actions across the intrusion lifecycle and map observed behavior to the MITRE ATT&CK framework.

---

## Environment

- Dataset: Splunk BOTS v2  
- Network: Windows Active Directory domain (frothly.local)  
- Primary affected host: MERCURY  
- Log sources:  
  - Windows Security logs  
  - Sysmon  
  - WinRM / PowerShell logs  
  - Registry telemetry  

---

## Investigation Scope

The investigation focuses on identifying:

- Initial unauthorized access on MERCURY  
- Remote execution via WinRM / PowerShell  
- Persistence mechanisms  
- Defense evasion techniques  
- System and network discovery activity  
- Data exfiltration behavior  

The dataset does not contain evidence of the original external compromise vector.  
The earliest confirmed malicious activity begins with authenticated remote access and command execution on MERCURY.

---

## Key Findings (High-Level)

Analysis shows that the attacker:

- Executed remote commands via WinRM  
- Deployed obfuscated PowerShell payloads with AMSI bypass  
- Modified scheduled tasks and registry locations  
- Performed network enumeration  
- Exfiltrated data using FTP  

These behaviors indicate a post-compromise intrusion focused on maintaining access and extracting data from the environment.

---

## Outcome

This investigation reconstructs the full attack chain on MERCURY and maps each phase to MITRE ATT&CK techniques.  
The case demonstrates practical SOC analysis including host compromise validation, persistence detection, and exfiltration identification using SIEM telemetry.

---

**Analyst:** Dimitrios Anastasiou  
**Role:** Junior SOC Analyst (training)  
**Dataset:** Splunk BOTS v2  
