End-to-End Data Analysis Project: SQL to Power BI

Table of Contents
1. Project Overview
2. Data Sources and Setup
3. Database Creation and SQL Queries
4. Power BI Integration and Data Modeling
5. Dashboard Design and Visualization
6. Key Insights and Analysis
7. Future Improvements
8. Conclusion

Project Overview
This project demonstrates the complete process of data analysis and visualization using SQL and Power BI. The main objective is to organize and visualize data for effective decision-making regarding budget management, project performance, and employee distribution across departments.

Key Questions Addressed:
Which projects and departments are at risk of being over budget or underperforming?
Can the current year's budget cover all expenses?
How do different departments compare in terms of project cost and budget variance?

Data Sources and Setup

Datasets Used:
completed_projects: Details on projects that have been completed, including project costs and duration.
departments: Information on department names and budget allocations.
employees: Employee data including names, job titles, and salaries.
Head_Shots: Contains URLs to employee headshots.
project_assignments: Mapping of employees to their respective projects.
projects: General information on all projects, both completed and upcoming.
upcoming_projects: Data on projects that are planned or in progress, including budgeted costs.

Setup:
Imported the above CSV files into a SQL database to create the necessary tables.
Structured the data with appropriate keys to establish relationships between tables.
Cleaned and transformed the data using SQL to prepare it for analysis in Power BI.

Database Creation and SQL Queries
Step 1: Creating the Database
Imported data from the provided CSV files.
Created tables for each dataset and established relationships based on foreign keys.
Step 2: Writing SQL Queries
Utilized JOIN operations to link employees with their project assignments, departments, and project details.
Implemented CTEs (Common Table Expressions) to simplify complex transformations and calculations.
Generated calculated columns for metrics such as total project cost, budget variance, and employee project involvement.

'''SQL Code
---PROJECT STATUS

WITH project_status AS (
SELECT
project_id,
project_name,
project_budget,
'upcoming' as status
FROM [upcoming projects]
UNION
SELECT
project_id,
project_name,
project_budget,
'completed' as status
FROM completed_projects)


--big table
SELECT 
e.employee_id,
e.first_name,
e.last_name,
e.salary,
e.job_title,
d.Department_Name,
d.Department_budget,
d.Department_goals,
pa.project_id,
p.project_name,
p.status,
p.project_budget

FROM employees e
JOIN departments d 
on e.department_id = d.Department_ID
JOIN project_assignments pa
on pa.employee_id = e.employee_id
JOIN project_status p
ON p.project_id = pa.project_id
'''

Power BI Integration and Data Modeling

Step 3: Connecting to Power BI
--Connected Power BI to the SQL database for dynamic data updates and visualization.
--Imported the employee headshots CSV file to add images to the dashboard for enhanced visualization.

Step 4: Data Modeling
--Established relationships between tables, such as linking project assignments to employee data and project details.
--Added calculated columns for total project costs and department budget variances.

Dashboard Design and Visualization
Step 5: Building the Dashboard
Designed an interactive dashboard showcasing key metrics and visualizations
--Project Cost Distribution: Pie chart displaying the cost distribution among various departments.
--Project Status & Cost Distribution: Donut chart illustrating the status and cost distribution of completed and upcoming projects.
--Employee Details: Displays individual employee data, including their role, department, and salary.
--Budget Variance Analysis: Table highlighting departments at risk of overspending.

Step 6: Customization
--Applied color formatting and layout adjustments for improved readability and aesthetic appeal.
--Incorporated interactive features such as slicers for department and project status filtering.

Key Insights and Analysis

Budget Variance Analysis:
--The Sales department has the highest positive budget variance, indicating efficient budget management.
--IT and HR departments are close to overspending, requiring closer budget monitoring.

Project Performance:
--Most costly project: Product Launch in the Sales department, indicating high investment.
--Project with the least expenditure: Social Media Strategy, possibly suggesting underfunding or efficiency.
--Employee Distribution and Costs:
The highest salary costs are in the Sales department, likely due to a larger workforce and high-value projects.

Future Improvements
--Data Granularity: Include more detailed time-based data (monthly, quarterly) for a more granular trend analysis.
--Predictive Modeling: Implement predictive analytics to forecast potential budget overruns or project delays.
--Automation: Set up scheduled data refreshes in Power BI for real-time updates.

Conclusion
This end-to-end data analysis project showcases the use of SQL for data preparation and Power BI for visualization. The resulting dashboard provides actionable insights into budget management, project performance, and employee allocation, aiding strategic decision-making.