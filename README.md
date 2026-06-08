# Wazuh-Soc-Detection-Lab

=======================

Security Monitoring & Incident Response 
---------------------------------------------------------

**by Abin Jose** | GitHub / LinkedIn  
**Published:** June 2026

What This Is
------------

A fully functional Security Operations Center (SOC) lab built from scratch. I deployed a real SIEM (Wazuh), connected Windows and Linux endpoints, executed 5 real attacks, detected them live, investigated the alerts, and wrote professional incident reports

Lab Architecture
----------------

`┌─────────────────────────────────────────────────────────────┐
│ Virtualization Host                                         │
│                                                             │
│  ┌──────────────┐   ┌──────────────┐   ┌──────────────┐     │
│  │ WAZUH-SRV    │   │ WIN-ENDPOINT │   │ ATTACKER     │     │
│  │ Wazuh Server │   │ Windows 10   │   │ Kali Linux   │     │
│  │ Ubuntu 22.04 │   │ 192.168.0.103 │   │ 192.168.0.105 │     │
│  │ 192.168.0.106 │   │ Wazuh Agent  │   │ Hydra/Nmap   │     │
│  │ SIEM         │   │              │   │ Netcat       │     │
│  └──────────────┘   └──────────────┘   └──────────────┘     │
│                                                             │
│      Host-Only / Lab Network: 192.168.0.1/24               │
└─────────────────────────────────────────────────────────────┘`

Tools Used
----------

| Tool              | Purpose                                       |
|-------------------|-----------------------------------------------|
| Wazuh 4.x         | SIEM — log collection, correlation, alerting  |
| VirtualBox / Hyper-V / VMware | Hypervisor — running lab VMs      |
| Ubuntu Server 22.04 | Wazuh server OS                             |
| Windows 10 / 11   | Victim endpoint (monitored)                   |
| Kali Linux        | Attacker machine                              |
| Hydra             | Brute force attacks                           |
| Nmap              | Port scanning / reconnaissance                |
| Netcat            | Data exfiltration listener                    |
| PowerShell        | Attack simulation on Windows                  |
| Sysmon (optional) | Enhanced Windows telemetry                    |

Attacks Executed & Detected
---------------------------

| # | Attack                        | Tool                  | Wazuh Rule (example)                    | Severity |
|---|------------------------------|-----------------------|-----------------------------------------|----------|
| 1 | Brute Force RDP / SSH       | Hydra                 | 60204 — Multiple Windows Logon Failures | 🔴 High |
| 2 | Port Scan                   | Nmap                  | 4151 — Multiple Firewall Drop Events    | 🟡 Medium |
| 3 | Malicious PowerShell Script | PowerShell            | 91815 — Suspicious PowerShell Activity  | 🟡 Medium |
| 4 | Privilege Escalation        | net.exe / runas       | 60170 — Users Group Changed             | 🔴 High |
| 5 | Data Exfiltration           | PowerShell + Netcat   | 10002 — TcpClient Exfiltration (custom) | 🔴 High |

Incident Reports
----------------

Each attack has a complete incident report documenting what happened, how it was detected, evidence collected, impact, response actions, and lessons learned. 

- IR-001 — Brute Force Attack  
- IR-002 — Port Scan  
- IR-003 — Malicious PowerShell Execution  
- IR-004 — Privilege Escalation  
- IR-005 — Data Exfiltration  



Screenshots
-----------

All evidence screenshots (alerts, dashboards, attack consoles, and reports) are stored in the `screenshots/` folder.



Key Takeaways
-------------

- Deployed and configured an open-source SIEM (Wazuh) from scratch in a home lab.  
- Gained hands-on experience with Windows security events, PowerShell logging, and Wazuh rules. 
- Wrote and tuned custom detection rules to close real detection gaps observed during testing.   
- Produced multiple incident reports following industry SOC formats, demonstrating detection, analysis, and response skills.  

Repo Structure
--------------

`Wazuh-Soc-Detection-Lab/  
├── README.md  
├── Screenshots/   
└── Incident-Reports/  
   

Built as a portfolio project to demonstrate practical SOC analyst skills — log analysis, SIEM configuration, threat detection, and incident response, inspired by the structure of other Wazuh SOC labs. 


