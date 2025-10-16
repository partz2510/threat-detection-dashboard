
# Threat detection dashboard (Demo Version)

This project demonstrates log ingestion and analysis using **Splunk Free Demo**.

## 🔹 Dashboard Overview

The **Threat Detection Dashboard** visualizes log data from multiple sources:

### 1️⃣ Failed Login Attempts
- Detects repeated failed login attempts from operating system logs.
- Visualization: **Bar Chart**
- Example:
- 
![Failed Login Chart](assets/failed_logins_chart.png)

### 2️⃣ Firewall Blocks
- Displays blocked connection attempts and reasons (e.g., brute force, multiple failed logins).  
- Visualization: **Pie Chart**
- Example:
- 
![Firewall Pie Chart](https://github.com/partz2510/threat-detection-dashboard/blob/main/assets/firewall_table.png?raw=true)

### 3️⃣ Application Errors
- Tracks authentication timeouts and multiple login attempts in applications.  
- Visualization: **Column Chart**
- Example:
![App Errors](https://github.com/partz2510/threat-detection-dashboard/blob/main/assets/apps_errors_chart.png?raw=true)

### 4️⃣ Multi-Source Correlation
- Correlates events across OS, firewall, and application logs to highlight suspicious IP activity.  
- Visualization: **Line Chart / Table**
- Example:
![Multi-Source Table](assets/multi_source_table.png)





