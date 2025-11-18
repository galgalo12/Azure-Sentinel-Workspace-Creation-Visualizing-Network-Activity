### 🔍 Visualizing Network Activity, Identity Events, & Malicious Flows with Microsoft Sentinel

## 📌 Overview
This project demonstrates how to build a Microsoft Sentinel and visualize key security telemetry using **Azure Workbooks and KQL**. The goal is to enable analysts to quickly interpret network security data through **geographic maps**, identity activity charts, and incident investigation visualizations.

This lab simulates a real SOC workflow, including:
- World map visualization of network activity
- Entra ID sign-in tracking (success/failure)
- VM authentication failure analysis
- Azure resource creation monitoring
- Malicious inbound traffic detection

The project is aligned to **MITRE ATT&CK**, SOC analysis workflows, and security monitoring best practices.

---

## 🎯 Objective
Create a Sentinel workspace + workbook dashboard that provides:
✔ Geographic threat visibility  
✔ Identity access insights  
✔ Resource creation monitoring  
✔ Inbound attack visibility  
✔ Live/near-real time detection capability  

---

## ⚙️ Logs Ingested
| Source | Purpose |
|--------|---------|
| Entra ID (Azure AD) | Successful & failed authentication |
| Azure Resource Manager Logs | Resource creation & change tracking |
| NSG Flow Logs | Network activity & malicious inbound traffic |
| VM Security Events | Authentication attempts & brute force |

---

## 📊 Workbooks Included (JSON)
| Workbook | Description |
|----------|-------------|
| Entra Login Success | Map of successful logins by IP | [Directory-Login-Successes.json](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Successes.json) |
| Entra Login Failure | Credential misuse / brute force investigation |
| Azure Resource Creation | Track & audit infrastructure deployment |
| VM Authentication Failures | Detect access attempts on compute resources |
| Malicious Inbound Flows | Map origin of malicious traffic |

---

## 📎 Reference Workbooks (based on public examples)

These JSON files are used as inspiration:
- Directory Login Successes  
- Directory Login Failures  
- Azure Resource Creation  
- VM Authentication Failures  
- Allowed Malicious Inbound Flows  

Source Repository: (`credits to Josh Madakor`)

---

## 🧠 Skills Demonstrated
### 🔐 Security Engineering & SIEM
- Azure Sentinel workspace deployment
- Log source onboarding
- Identity & network monitoring
- Attack surface visibility

### 📈 Data Visualization
- Azure Workbooks
- Custom maps, time charts, and conditional formatting
- SOC dashboard design and layout

### 🧵 KQL + Threat Hunting
- Advanced log analysis
- Threat mapping to MITRE ATT&CK
- IP/location analysis
- Network flow inspection

### 🧰 Cloud & DevOps
- GitHub version control
- Infrastructure logging pipelines
- JSON-based dashboard deployment

---

## MITRE ATT&CK Mapping
| Technique | Use Case |
|-----------|----------|
| **T1078** | Account abuse / login failures |
| **T1136** | Resource creation misuse |
| **T1190** | Malicious inbound flow exploit attempts |
| **T1021** | VM login failure / lateral movement |
| **T1040** | Network monitoring |

---

## 🚀 Deployment
### Import workbooks manually:
1. Microsoft Sentinel → Workbooks
2. Upload workbook JSON
3. Connect parameters to relevant tables
4. Save + pin where needed

---

## Future Enhancements
- Logic Apps for automatic alert response
- Analytics rule automation
- IP enrichment (Threat Intelligence)
- External API enrichment (OTX, AbuseIPDB, VirusTotal)
- UEBA integration for user analytics

---

## 📜 License
MIT License — free to use and modify.
