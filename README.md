# 🔍 Visualizing Network Activity, Identity Events, & Malicious Flows with Microsoft Sentinel

This project demonstrates how to use **Microsoft Sentinel** to visualize key security telemetry through **Azure Workbooks** and **KQL queries**. The goal is to help analysts quickly interpret network and identity events using:

- 🌍 Geographic mapping  
- 🔐 Authentication activity tracking  
- ☁️ Resource monitoring  
- 🚨 Incident-focused visualizations  

We use logs generated within our environment—some from students, others from real-world internet threat actors—to build **world map visualizations** based on originating IP addresses. These maps provide a clear picture of what's happening across the network and where activity is coming from geographically.

Although this lab focuses on a few core examples, you can build map visualizations for **any log type**. What you choose to track depends on the needs and priorities of your organization.

This SOC-focused lab simulates real operational workflows, including:

- 🌍 **World map visualization of network activity**  
- 🔐 **Entra ID sign-in tracking** (successful & failed authentication attempts)  
- 💻 **VM authentication failure analysis**  
- ☁️ **Azure resource creation monitoring**  

These visualizations help analysts detect anomalies, identify suspicious logins, and understand global attack patterns in seconds.

---

## 📊 Workbooks Included (JSON)

| Workbook | Description |
|----------|-------------|
| **[Entra Login Success](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Successes.json)** | Map of successful logins by IP |
| **Entra Login Failure** | Investigate failed authentications, brute force patterns, and misuse |
| **Azure Resource Creation** | Track & audit new infrastructure deployments |
| **VM Authentication Failures** | Detect unauthorized access attempts on compute resources |
| **Malicious Inbound Flows** | Map the geographic origin of hostile traffic |

---

🚀 Deployment Instructions
Option 1 – Manual Workbook Import

Go to Microsoft Sentinel → Workbooks

Click Add Workbook

Click Edit

Add a query component

Paste the KQL from the JSON template

<img src="https://github.com/user-attachments/assets/c4f462a9-3ee7-4fe8-aaed-9aeeea332f71" width="350">

Run query → adjust visualization (map, chart, etc.)

<img  src="https://github.com/user-attachments/assets/7a5c6248-83d6-4424-a241-81102482cddd" width="420">

Save + pin to dashboard

## 🔍 Step 4 — Run the KQL Query in Microsoft Sentinel

Navigate to **Microsoft Sentinel → Logs** and run the KQL query provided in this project.

Once executed, the query aggregates sign-in activity grouped by **user** and **location**.

### ✅ Query Output Summary

The results indicate that the user has successfully authenticated multiple times.

**Successful Logins:** `6`  
**All login attempts originated from the same location:**

- **City:** Chicago  
- **Country:** US  
- **Latitude:** 41.8488  
- **Longitude:** -87.6712  

### 📘 What This Shows

This KQL query helps validate that:

- The user’s authentication activity is **consistent** and originates from a **single geolocation**.
- No anomalous or suspicious geo-patterns were observed in these logins.

### 🛡️ Why This Matters

Understanding geolocation data is crucial for:

- ✅ Detecting unusual or risky sign-in behavior  
- ✅ Building **geolocation-based visualizations** (e.g., Maps, Workbooks)  
- ✅ Investigating suspicious authentication activity  
- ✅ Correlating user identity events with geographic patterns

<img  src="https://github.com/user-attachments/assets/30f3141c-c34f-491c-aea0-6d1bd819b499" width="420"/>


This information becomes an essential part of threat detection, incident investigations, and building SOC dashboards.

### 📘 Additional Logs Added

Here is the section I added after completing some of the log creation steps.  
You can view the corresponding screenshot below.

To finish the setup, simply repeat the same step-by-step process for the remaining logs in the **Azure Workbook**.

<img src="https://github.com/user-attachments/assets/0b7f66d2-b350-4a7f-b65f-b2cc6afa4070" width="520" />


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

## Future Enhancements
- Logic Apps for automatic alert response
- Analytics rule automation
- IP enrichment (Threat Intelligence)
- External API enrichment (OTX, AbuseIPDB, VirusTotal)
- UEBA integration for user analytics

---

