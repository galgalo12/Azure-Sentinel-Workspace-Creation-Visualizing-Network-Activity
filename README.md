# 🔍 Visualizing Network Activity, Identity Events, & Malicious Flows with Microsoft Sentinel

This project demonstrates how to use **Microsoft Sentinel** to visualize key security telemetry via **Azure Workbooks** and **KQL queries**. It helps analysts quickly interpret network and identity events using:

- 🌍 Geographic mapping  
- 🔐 Authentication activity tracking  
- ☁️ Resource monitoring  
- 🚨 Incident-focused visualizations  

We leverage logs generated from simulated student activity and real-world threat data to build **world map visualizations** based on originating IP addresses. These maps provide a clear picture of global activity across the network.  

While this lab covers core examples, the same approach can be applied to **any log type**, depending on your organizational priorities.

This SOC-focused lab simulates real operational workflows, including:

- 🌍 **World map visualization of network activity**  
- 🔐 **Entra ID sign-in tracking** (successful & failed attempts)  
- 💻 **VM authentication failure analysis**  
- ☁️ **Azure resource creation monitoring**  

These visualizations allow analysts to detect anomalies, suspicious logins, and understand global attack patterns in seconds.  

---

## 📊 Workbooks Included (JSON)

| Workbook | Description |
|----------|-------------|
| **[Entra Login Success](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Successes.json)** | Map of successful logins by IP |
| **[Entra Login Failure](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Directory-Login-Failures.json)** | Investigate failed authentications, brute-force patterns, and misuse |
| **[Azure Resource Creation](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Azure-Resource-Creation.json)** | Track & audit new infrastructure deployments |
| **[VM Authentication Failures](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/VM-Authentication-Failures.json)** | Detect unauthorized access attempts on compute resources |
| **[Malicious Inbound Flows](https://github.com/joshmadakor1/lognpacific-public/blob/main/cyber-range/sentinel/Allowed-Inbound-Malicious-Flows.json)** | Map the geographic origin of hostile traffic |

---

## 🚀 Deployment Instructions

### Option 1 — Manual Workbook Import

1. Navigate to **Microsoft Sentinel → Workbooks**  
2. Click **Add Workbook**  
3. Click **Edit**  
4. Add a **query component**  
5. Paste the KQL from the JSON template  

<img width="1401" height="676" alt="Screenshot 2025-12-09 at 2 41 47 AM" src="https://github.com/user-attachments/assets/e43e5169-f3d3-4eb0-a82a-5c858eb52586" />

6. Run query → adjust visualization (map, chart, etc.)  

<img src="https://github.com/user-attachments/assets/7a5c6248-83d6-4424-a241-81102482cddd" width="420">

7. Save & pin to dashboard  

---

## 🔍 Run the KQL Query in Microsoft Sentinel

Navigate to **Microsoft Sentinel → Logs** and execute the KQL query. It aggregates sign-in activity by **user** and **location**.`

    ``kusto
    SigninLogs
    | where ResultType == 0
    | summarize LoginCount = count() by 
        Identity,
        Latitude = tostring(LocationDetails["geoCoordinates"]["latitude"]),
        Longitude = tostring(LocationDetails["geoCoordinates"]["longitude"]),
        City = tostring(LocationDetails["city"]),
        Country = tostring(LocationDetails["countryOrRegion"])
    | project 
        Identity,
        Latitude,
        Longitude,
        City,
        Country,
        LoginCount,
        friendly_label = strcat(Identity, " - ", City, ", ", Country)

# Successful Logins: 6

All login attempts originated from the same location:

- **City:** Chicago  
- **Country:** US  
- **Latitude:** 41.8488  
- **Longitude:** -87.6712  

---

## 📘 Insights

This query demonstrates:

- ✅ Consistent authentication activity from a single geolocation  
- ✅ No anomalous or suspicious geo-patterns in logins  

---

## 🛡️ Importance

Understanding geolocation data enables:

- Detecting unusual or risky sign-ins  
- Building map-based visualizations for dashboards  
- Investigating suspicious authentication activity  
- Correlating user identity events with geographic patterns  

<img src="https://github.com/user-attachments/assets/30f3141c-c34f-491c-aea0-6d1bd819b499" width="420"/>

---

## 📘 Additional Logs Added

After creating initial logs, you can repeat the same step-by-step process to add remaining logs in Azure Workbooks.

<img src="https://github.com/user-attachments/assets/0b7f66d2-b350-4a7f-b65f-b2cc6afa4070" width="520"/>

---

## MITRE ATT&CK Mapping

| Technique | Use Case |
|-----------|----------|
| T1078     | Account abuse / login failures |
| T1136     | Resource creation misuse |
| T1190     | Malicious inbound flow exploit attempts |
| T1021     | VM login failure / lateral movement |
| T1040     | Network monitoring |

---

## Future Enhancements

- Logic Apps for automatic alert response  
- Analytics rule automation  
- IP enrichment via Threat Intelligence  
- External API enrichment (OTX, AbuseIPDB, VirusTotal)  
- UEBA integration for user behavior analytics

