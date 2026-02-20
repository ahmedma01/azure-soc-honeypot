# 🛡️ Azure SOC & Threat Intelligence Honeypot

A cloud-based Security Operations Centre (SOC) lab built on Microsoft 
Azure, designed to collect and analyse real-world attack data from the internet.

## 🛠️ Tech Stack
- **Cloud:** Microsoft Azure
- **SIEM:** Microsoft Sentinel
- **Log Management:** Log Analytics Workspace
- **Query Language:** KQL (Kusto Query Language)
- **Visualisation:** Azure Workbooks

## 📐 Architecture
- Deployed a vulnerable Windows VM as a honeypot with intentionally open NSG firewall rules
- Configured Log Analytics Workspace as a central log hub for the VM
- Wrote custom KQL queries to parse logs and extract geographic data from unauthorised login attempts
- Built an interactive Azure Workbook displaying a live global attack map

## 🎯 What I learned
- How SIEM tools ingest and correlate security logs
- How to write KQL queries to investigate real attack data
- How threat actors behave when targeting exposed cloud infrastructure
- Translating raw log data into actionable visual intelligence
