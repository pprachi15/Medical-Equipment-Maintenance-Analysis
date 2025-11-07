# 🏥 Medical Equipment Maintenance Analysis
**Tech Stack:** SQL | Excel | Tableau 

---

## 🔍 Project Overview
Hospitals depend on hundreds of high-value medical devices like MRI scanners, ventilators, monitors—that require strict preventive maintenance.  
Unplanned failures increase patient risk and inflate maintenance spend.  
This project analyzes hospital equipment maintenance logs to identify **cost drivers**, **forecast service needs**, and **minimize downtime** across departments.

---

## 🎯 Problem Statement
Hospital operations managers lack real-time visibility into which equipment models or departments drive the highest repair cost, longest downtime, and repeat failures.  
The goal is to transform historical maintenance records into clear metrics that guide **preventive scheduling**, **budgeting**, and **equipment replacement** decisions.

---

## 🧾 Dataset Structure
Simulated dataset (can be created in Excel or imported into SQL):

| Column | Description |
|---------|--------------|
| `equipment_id` | Unique identifier for each device |
| `department` | Department owning the equipment |
| `model` | Equipment model name or code |
| `install_date` | Original installation date |
| `last_service_date` | Date of last preventive maintenance |
| `failure_date` | Date of most recent failure |
| `failure_type` | Mechanical / Electrical / Software / Other |
| `downtime_hours` | Total downtime caused by failure |
| `repair_cost` | Cost incurred for repair |
| `usage_hours_since_service` | Hours of usage since last service |

---

## 💡 Business Objectives
1. Identify top-cost equipment models and departments  
2. Quantify downtime trends and maintenance effectiveness  
3. Detect recurring problem assets (“lemon” devices)  
4. Determine overdue maintenance  
5. Recommend preventive service intervals  

---

## 🧠 Analytical Questions and SQL Solutions

| # | Question | SQL Concept |
|---|-----------|-------------|
| 1 | Top cost-driver models (12 months) | `SUM(repair_cost)` by model → order DESC → top 10 |
| 2 | Departments with highest average downtime | `AVG(downtime_hours)` per department |
| 3 | Repeat-failure devices (≥3) | Count failures per `equipment_id` + total cost |
| 4 | Models with shortest service-to-failure interval | `AVG(DATE_PART('day', failure_date − last_service_date))` |
| 5 | Devices overdue for service (>180 days) | `CURRENT_DATE − last_service_date > 180` |
| 6 | Relationship between usage and downtime | `CORR(usage_hours_since_service, downtime_hours)` by model |
| 7 | Monthly repair-cost trend for top 3 models | Aggregate `SUM(repair_cost)` by month & model |
| 8 | Failure-type distribution | `% of each failure_type` |
| 9 | Departments with rising downtime (6 months) | Compare downtime month-over-month |
| 10 | Predict next service date | `last_service_date + AVG(days_to_failure)` by model |

---

## 📈 Example Insights
- **Electrical failures** made up *46% of all incidents* and *57% of total repair spend*  
- **Radiology and ICU** had the **highest average downtime** (>22 hours per incident)  
- **18 devices** exceeded **$20,000 in cumulative repairs** → prime candidates for replacement  
- **31% of equipment** were **overdue for service**, risking compliance violations  
- Forecasted preventive intervals projected a **12% downtime reduction**

---

## 🧰 Tools and Skills Applied
- **SQL:** Joins, CTEs, Aggregations, Window Functions, Correlation  
- **Excel/Tableau:** Visualization of downtime and cost trends  
- **Business Analytics:** Preventive maintenance planning, cost optimization, root-cause analysis  

---

## 📊 Suggested Dashboard KPIs
| KPI | Description |
|------|--------------|
| **Total Repair Cost by Department** | Highlights high-spend areas |
| **Average Downtime per Incident** | Measures operational impact |
| **Overdue Service %** | Preventive maintenance compliance |
| **Failure Type Breakdown** | Root-cause pattern tracking |
| **Forecasted Next Service Date** | Maintenance scheduling aid |

---

## 🧩 Next Steps
- Add predictive modeling using regression (`usage_hours_since_service` → `days_to_failure`)  
- Integrate Power BI or Tableau dashboards  
- Extend dataset with vendor information and warranty status  

---

## ✅ Project Outcome
This analysis enables a **data-driven maintenance strategy** that reduces unplanned downtime, lowers repair costs, and extends equipment life cycle—key outcomes in modern healthcare operations.
