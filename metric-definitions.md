# Metric Definitions - Enhancing IT Utilization Dashboard

This document defines key performance indicators and their DAX formulas used to evaluate IT application, infrastructure, and database utilization from 2014 to 2018.

---

## 1.1 Number of Integrated Applications

- *Metric:* Number_of_Apps
- *Definition:* Total count of IT applications that have been integrated.
- *DAX Formula:*
DAX
Number_of_Apps = COUNTROWS('Apps')

- *Source Table:* Integrated Applications

---

## 1.2 Application Integration Achievement Percentage

- *Metric:* Achievement_Percentage
- *Definition:* Percentage of actual integrated applications compared to target.
- *DAX Formula:*
DAX
Achievement_Percentage = DIVIDE([Number_of_Apps], [Target_Apps], 0)

- *Target Metric:*
DAX
Target_Apps = SUM('Targets'[Target_App])

- *Source Table:* Integration Achievement

---

## 1.3 Application Uptime Percentage

- *Metric:* App_Uptime_Percentage
- *Definition:* Proportion of time applications were operational.
- *DAX Formula:*
DAX
App_Uptime_Percentage = DIVIDE([App_Uptime_Seconds], [App_Uptime_Seconds] + [App_Downtime_Seconds], 0)

- *Supporting Metrics:*
DAX
App_Uptime_Seconds = SUM('UptimeData'[Uptime_Seconds])
App_Downtime_Seconds = SUM('UptimeData'[Downtime_Seconds])


---

## 1.4 Network and Infrastructure Uptime Percentage

- *Metric:* Network_Uptime_Percentage
- *Definition:* Uptime of network and infrastructure systems.
- *DAX Formula:*
DAX
Network_Uptime_Percentage = DIVIDE([Network_Uptime_Seconds], [Network_Uptime_Seconds] + [Network_Downtime_Seconds], 0)

- *Supporting Metrics:*
DAX
Network_Uptime_Seconds = SUM('NetworkLogs'[Uptime_Seconds])
Network_Downtime_Seconds = SUM('NetworkLogs'[Downtime_Seconds])

- *Target:* 99.90%

---

## 1.5 Database Uptime Percentage

- *Metric:* Database_Uptime_Percentage
- *Definition:* Uptime rate of database systems.
- *DAX Formula:*
DAX
Database_Uptime_Percentage = DIVIDE([Database_Uptime_Seconds], [Database_Uptime_Seconds] + [Database_Downtime_Seconds], 0)

- *Supporting Metrics:*
DAX
Database_Uptime_Seconds = SUM('DatabaseLogs'[Uptime_Seconds])
Database_Downtime_Seconds = SUM('DatabaseLogs'[Downtime_Seconds])


---

## 1.6 New Application Completion Percentage

- *Metric:* New_App_Completion_Percentage
- *Definition:* Ratio of completed new applications to target.
- *DAX Formula:*
DAX
New_App_Completion_Percentage = DIVIDE([New_App_Achievement], [New_App_Target], 0)

- *Supporting Metrics:*
DAX
New_App_Achievement = SUM('Projects'[Completed_New_Apps])
New_App_Target = SUM('Projects'[Target_New_Apps])

- *Productivity Metric:*
DAX
Resource_Productivity = DIVIDE([New_App_Achievement], [Total_Resources], 0)


---

## 1.7 New Application Implementation Completion

- *Metric:* New_App_Implementation_Completion
- *Definition:* Measures implementation progress normalized by resources.
- *DAX Formula:*
DAX
New_App_Implementation_Completion = DIVIDE([New_App_Implementation_Achievement], [Target_Implementation], 0)

- *Per Resource:*
DAX
Implementation_Per_Resource = DIVIDE([New_App_Implementation_Achievement], [Resources_Used], 0)


---

## Overall KPI Achievement

- *Metric:* KPI_Achievement_Percentage
- *Definition:* Measures cumulative performance across key indicators.
- *DAX Formula:*
DAX
KPI_Achievement_Percentage = DIVIDE([Total_Achievement], [Total_Target], 0)

- *Supporting Metrics:*
DAX
Total_Achievement = SUM('KPI'[Actual])
Total_Target = SUM('KPI'[Target])


---
