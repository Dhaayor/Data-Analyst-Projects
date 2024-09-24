# 💼 End-to-End Data Analysis Project: SQL to Power BI

## 📋 Project Overview

This project showcases a complete data analysis workflow, from data ingestion and transformation using SQL to visualization and interactive dashboard creation in Power BI. The objective is to provide actionable insights into project performance, budget management, and employee distribution across departments.

## 🔍 Key Questions Addressed
- **Which projects and departments are at risk of being over budget or underperforming?**
- **Is the current year's budget sufficient to cover all expenses?**
- **How do different departments compare in terms of project costs and budget variance?**

## 🛠️ Tools and Technologies Used
- **SQL**: For data extraction, transformation, and analysis.
- **Power BI**: For building interactive dashboards and visualizations.
- **CSV Files**: Source data for employees, projects, budgets, and departments.

## 📊 Data Sources and Structure
The project uses the following datasets:
- **`completed_projects`**: Information on completed projects, including costs and duration.
- **`departments`**: Details of departments with budget allocations.
- **`employees`**: Employee information, including roles, salaries, and departments.
- **`Head_Shots`**: URLs for employee headshots.
- **`project_assignments`**: Mapping of employees to their respective projects.
- **`projects`**: General information on all projects (both completed and upcoming).
- **`upcoming_projects`**: Data on planned or in-progress projects, including budgeted costs.

## 🗂️ Project Workflow

1. **Data Ingestion and Cleaning**:
   - Imported multiple CSV files into a SQL database.
   - Cleaned and transformed the data using SQL queries, including `JOIN`, `CTE`, and aggregation functions.

2. **SQL Queries and Analysis**:
   - Wrote complex SQL queries to analyze budget variance, project performance, and employee allocation.
   - Used Common Table Expressions (CTEs) and advanced SQL functions to create derived columns for further analysis.
''''sample sql query
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

3. **Power BI Integration**:
   - Connected the cleaned data from SQL to Power BI for dynamic reporting.
   - Created relationships between tables in Power BI to enable comprehensive data analysis.

4. **Dashboard Creation**:
   - Designed an interactive dashboard to visualize key metrics such as project costs, budget variance, and employee details.
   - Applied custom formatting, color schemes, and slicers for an intuitive user experience.

## 🔑 Key Insights
- **Budget Management**: The Sales department has the highest positive budget variance, indicating efficient cost management. Conversely, the HR department is nearing its budget limit.
- **Project Analysis**: The ‘Product Launch’ project in the Sales department is the most expensive, while the ‘Social Media Strategy’ project in Marketing has the lowest budget.
- **Employee Allocation**: Sales department has the highest salary allocation, suggesting a focus on resource-intensive projects.

## 🎯 Future Enhancements
- **Data Granularity**: Include monthly or quarterly data for more detailed trend analysis.
- **Predictive Analysis**: Implement predictive models to forecast project success and potential budget overruns.
- **Automation**: Enable automated data refreshes in Power BI to ensure real-time dashboard updates.

## 📈 Dashboard Preview
![Data Visualization board](https://github.com/user-attachments/assets/da1d4ca2-729d-444b-9c6b-b590af8a62f9)


## 📂 How to Run the Project
1. Clone the repository.
2. Import the provided CSV files into your SQL database.
3. Execute the SQL scripts in the `sql_queries` folder to set up the database.
4. Open the Power BI file (`.pbix`) and connect it to the SQL database.
5. Explore the interactive dashboard and insights.

## 📝 License
This project is licensed under the MIT License. 
