
# threat-detection-dashboard
Splunk project for threat detection &amp; correlation
=======
# Threat detection dashboard (Demo Version)

This project demonstrates log ingestion and analysis using **Splunk Free Demo**.

## Dashboard Panels

### 1. Failed Login Attempts
![Failed Login Chart](assets/failed_logins_chart.png)

### 2. Firewall Blocks
![Firewall Pie Chart](assets/firewall_pie.png)

### 3. Application Login Errors
![App Errors](assets/app_errors_chart.png)

### 4. Multi-Source Correlation
![Multi-Source Table](assets/multi_source_table.png)

## SPL Queries

#### Failed Logins
```spl
index=threat_demo sourcetype="operating system" "Failed password"
| rex field=_raw "from\s(?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| where count > 2
| rename src_ip as "Attacker IP", count as "Failed Attempts"

Firewall Blocks
index=threat_demo sourcetype="network and security" "BLOCK"
| rex field=_raw "(?<src_ip>\d+\.\d+\.\d+\.\d+):\d+\s->"
| stats count by src_ip, REASON
| rename src_ip as "Blocked IP", count as "Block Count"

Application Errors
index=threat_demo sourcetype="application" ("Authentication timeout" OR "Multiple login attempts")
| rex field=_raw "from\s(?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| rename src_ip as "Source IP", count as "App Error Count"

Multi-Source Correlation
(index=threat_demo sourcetype="operating system" "Failed password")
OR (index=threat_demo sourcetype="network and security" "BLOCK")
OR (index=threat_demo sourcetype="application" "Authentication timeout")
| rex field=_raw "(?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by sourcetype src_ip
| chart sum(count) over src_ip by sourcetype
>>>>>>> 904d887 (Update README.md)
