# 🛡️ Azure SOC & Threat Intelligence Honeypot

A cloud-based Security Operations Centre (SOC) lab built on Microsoft Azure,
designed to collect and analyse real-world attack data from the internet.
This project simulates how security teams detect, investigate, and visualise 
threats using industry-standard SIEM tooling.

## 📋 Overview
Rather than just learning about SIEM tools theoretically, I built a live 
environment where real attackers interact with an intentionally exposed VM. 
This generated genuine attack data that I could investigate, query, and 
visualise — mirroring how SOC analysts work in real organisations.

The project involved deploying a vulnerable Windows VM as a honeypot, 
configuring Microsoft Sentinel as the SIEM, writing KQL queries to extract 
geographic data from failed login attempts, and building a live attack map 
in Azure Workbooks.

## 🛠️ Tech Stack
| Tool | Purpose |
|------|---------|
| Microsoft Azure | Cloud platform |
| Windows VM | Honeypot target |
| Network Security Groups | Intentionally open firewall rules |
| Log Analytics Workspace | Central log ingestion and storage |
| Microsoft Sentinel | SIEM & threat detection |
| KQL | Log querying and analysis |
| Azure Workbooks | Attack visualisation and mapping |

## ✨ Key Features
- **Live Honeypot** — Real-world attack data collected from exposed VM
- **SIEM Integration** — Sentinel ingesting and correlating security logs
- **KQL Queries** — Custom queries extracting attacker geographic locations
- **Attack Map** — Interactive global map of live threats built in Azure Workbooks
- **NSG Analysis** — Intentionally misconfigured firewall to attract attacks

## 📸 Screenshots

### Live Global Attack Map
<img width="1408" height="678" alt="attack map" src="https://github.com/user-attachments/assets/0c7e18dd-43ef-4901-86d5-0a41aa0bf518" />

### KQL Query & Results
<img width="1920" height="852" alt="final kql running" src="https://github.com/user-attachments/assets/35a30a6d-4fc7-4345-9685-2e854d8383a3" />

> 📁 Additional screenshots (VM setup, NSG rules, Log Analytics, Sentinel) 
> available in the [screenshots folder](./screenshots/)

## 📐 How It Works
1. A Windows VM was deployed on Azure and NSG rules were opened to allow 
   inbound traffic — making it an intentional target
2. A **Log Analytics Workspace** was configured to ingest all security 
   logs from the VM
3. **Microsoft Sentinel** was connected as the SIEM, monitoring the 
   workspace for threats
4. Custom **KQL queries** were written to parse failed login logs and 
   extract attacker IP addresses and geographic locations
5. An **Azure Workbook** was built to plot attack origins on an 
   interactive world map in real time

## 🔍 KQL Query Example
```kql
SecurityEvent
| where EventID == 4625
| where TimeGenerated > ago(24h)
| extend Country = tostring(parse_json(tostring(AdditionalFields)).Country)
| summarize AttackCount = count() by Country, IpAddress
| sort by AttackCount desc
```

## 🔮 Future Improvements
- Configure custom Sentinel analytics rules to trigger alerts on 
  suspicious patterns
- Integrate threat intelligence feeds to enrich attacker IP data
- Deploy a Linux honeypot alongside the Windows VM for comparison
- Set up automated incident response playbooks using Logic Apps
- Expand logging to capture lateral movement simulation

## ❓ Why This Project?
I built this to:
- Understand how SIEM tools ingest, correlate, and surface security events
- See how real attackers behave when targeting exposed cloud infrastructure
- Practice writing KQL to investigate genuine attack data
- Learn how threat intelligence is visualised for SOC teams
- Gain hands-on Azure experience beyond just deploying VMs
