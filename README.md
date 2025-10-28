# 🚀 Azure Data Pipeline Project (ADF + Azure SQL + Power BI)

### 🌐 End-to-End Cloud Data Engineering & Analytics Workflow  
This project demonstrates an **end-to-end data pipeline solution** built using **Azure Data Factory (ADF)**, **Azure SQL Database**, and **Power BI**.  
It automates data ingestion, transformation, and reporting to monitor asset performance in real time.

---

## 🧠 Project Overview

**Objective:**  
Design and deploy a cloud-based ETL pipeline that:
- Ingests data from **Azure Blob Storage**
- Transforms and loads it into **Azure SQL Database**
- Visualizes operational KPIs using **Power BI**

---

## ⚙️ Workflow Architecture

**1. Source (Raw Data):**  
- CSV files stored in Azure Blob Storage container `RawData`

**2. Data Transformation & Loading:**  
- Managed by Azure Data Factory pipeline  
- Includes schema mapping, data validation, and load to Azure SQL table `AssetPerformanceData`

**3. Destination (SQL):**  
- Target: Azure SQL Database (`AzureSqlDatabase1`)  
- Stores transformed asset performance data

**4. Visualization (Power BI):**  
- Real-time analytics dashboard connected directly to SQL Database  
- Displays CPU/Memory metrics, downtime, and performance KPIs

---

## 🧩 Repository Structure

```plaintext
Azure-Data-Pipeline-Project-Pran/
├── factory/
│   ├── ARMTemplateForFactory.json
│   ├── ARMTemplateParametersForFactory.json
│   ├── VazeADF_ARMTemplateForFactory.json
│   ├── VazeADF_ARMTemplateParametersForFactory.json
│
├── linkedTemplates/
│   ├── ArmTemplate_master.json
│   ├── ArmTemplateParameters_master.json
│   ├── ArmTemplate_0.json
│
├── visuals/
│   ├── Asset_Performance_Azure.pbix
│   └── dashboard_preview.png
│
├── README.md
└── (future folders: datasets/, pipelines/, triggers/)
📊 Power BI Dashboard
Dashboard File: Asset_Performance_Azure.pbix

🖼️ Preview:

Key Metrics Visualized
KPI	Description
Avg CPU Usage (%)	Average CPU utilization across assets
Avg Memory Usage (%)	Average memory consumption
Uptime %	Ratio of uptime hours to total hours
Failure Count	Total recorded system failures
Downtime (hrs)	Total hours systems were unavailable

DAX Measures:

DAX
Copy code
Avg_CPU = AVERAGE(AssetPerformanceData[CPU_Usage_Percent])
Avg_Memory = AVERAGE(AssetPerformanceData[Memory_Usage_Percent])
Uptime_Percentage = DIVIDE(SUM(AssetPerformanceData[Uptime_Hours]), SUM(AssetPerformanceData[Total_Hours]), 0)
Failure_Rate_per_1000 = DIVIDE(SUM(AssetPerformanceData[Failure_Count]) * 1000, COUNTROWS(AssetPerformanceData), 0)
🧰 Tools & Technologies
Category	Tool
Data Orchestration	Azure Data Factory
Data Storage	Azure SQL Database
Data Source	Azure Blob Storage
Visualization	Power BI Desktop
Version Control	GitHub + Git Bash
Language	SQL, DAX, JSON

🔧 Deployment Instructions
Import ARM Template into Azure Data Factory
Navigate to Manage → ARM Template → Import

Upload the following files:

ARMTemplateForFactory.json

ARMTemplateParametersForFactory.json

Configure Linked Services
Source: Azure Blob Storage (Raw Data)

Destination: Azure SQL Database (AzureSqlDatabase1)

Trigger & Monitor Pipeline
Execute manually or use scheduled triggers

Monitor data flow success in ADF Monitor tab

🌟 Learning Outcomes
✔️ Hands-on with Azure Data Factory pipelines
✔️ Integration of Blob → SQL → Power BI
✔️ Practical use of ETL and DataOps principles
✔️ Exposure to ARM Templates for deployment automation
✔️ Experience in visual analytics with Power BI

🧠 Future Enhancements
Add CI/CD automation via Azure DevOps

Integrate data validation checks during ETL

Expand dashboard with predictive insights (Power BI + ML)

Include automated email alerts for failed pipeline runs

👨‍💻 Author
Pranav Vaze
