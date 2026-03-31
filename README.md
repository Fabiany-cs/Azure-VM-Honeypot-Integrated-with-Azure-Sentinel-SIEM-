# Azure VM Honeypot Integrated with Azure Sentinel (SIEM)
<h2>Description</h2>
<p>This project guides you through the creation of a honeypot environment in Azure, aimed at monitoring and analyzing brute force login attempts. By deploying a Windows 10 Pro Virtual Machine (VM) and integrating it with Azure Sentinel, Microsoft Defender for Cloud, and Log Analytics Workspaces, you'll be able to observe and analyze malicious login attempts in real-time. The project includes setting up logging, custom log creation, and visualization of geographic data using Azure Sentinel workbooks.</p>
<img width="1437" alt="Screenshot 2024-04-18 at 11 15 45 PM" src="https://github.com/Fabiany-cs/Azure-VM-Honeypot-Integrated-with-Azure-Sentinel-SIEM-/assets/107880960/a1cf81a2-08cc-49fb-a252-5061eec2b36f">

# Azure VM Honeypot Lab

## Description

This project deploys a purposely exposed Windows VM in Azure to attract and analyze real-world RDP brute force attacks. A PowerShell script captures every failed login attempt, enriches it with geolocation data via the ipgeolocation.io API, and writes it to a custom log file. Azure Monitor Agent ships the log to a Log Analytics Workspace where a Workbook visualizes attacker origins on a live world map.

> **Updated for 2025/2026** — The legacy Log Analytics Agent (MMA/OMS) was retired August 31, 2024. This version uses the current Azure Monitor Agent (AMA) + Data Collection Rule pipeline.

---

## Architecture

```
Internet attackers
       |
       v
  honeypot-vm  <-- Windows VM, firewall disabled, all ports open
       |
       v
  PowerShell script  <-- captures Event ID 4625, calls geo API
       |
       v
  C:\ProgramData\failed_rdp.log
       |
       v
  Azure Monitor Agent (AMA)  <-- auto-installed by Data Collection Rule
       |
       v
  Data Collection Endpoint + Data Collection Rule  <-- pipeline wiring
       |
       v
  FAILED_RDP_WITH_GEO_CL  <-- custom log table in Log Analytics Workspace
       |
       v
  Azure Workbook  <-- live world map of attacks
```

---

## Tools Used

- Microsoft Azure (Virtual Machine, Log Analytics Workspace, Azure Monitor Agent, Data Collection Rule, Azure Workbook)
- PowerShell
- KQL (Kusto Query Language)
- ipgeolocation.io API

---

## Files in This Repository

| File | Purpose |
|---|---|
| `PowerShell Log Exporter (GEO IP)` | Run on the VM — captures failed RDP logins and enriches with geo data |
| `Extract Log Query` | KQL query used to parse and visualize the raw log data |
| `sample-log.txt` | Sample log line used to define the custom table schema |

---

## Full Lab Guide

Step-by-step instructions for recreating this lab are available at: [your website link here]

---

## Credits

Original project concept by [Josh Madakor](https://github.com/joshmadakor1).

