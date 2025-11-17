# HR Analytics Dashbord
<img width="1090" height="430" alt="image" src="https://github.com/user-attachments/assets/ebde9076-7c69-40f6-acb9-c52ad084e767" />

## Introduction
The HR Analytics Dashboard was designed to analyze and visualize key workforce metrics for Bash Logistic, providing actionable insights into employee demographics, job distribution, and employment status. The goal of the project was to help HR managers make informed decisions regarding recruitment, retention, and workforce optimization through data-driven insights.

**_Disclaimer:_** This dataset is based on real data from Bash Logistics but has been modified and anonymized with the company’s permission to demonstrate the capabilities of a dynamic Excel dashboard.

### Excel Concept applied
- Advanced Excel Formulas: Utilized calculated measures and calculated columns using if() funtion
- Pivot Table: Used for quick Analysis
- Interactivity: Implemented a search bar feature to dynamically display employee details based on name input and quick button for easy access.
- Visuals: KPI Card, Picart, Bar Chart, Tables, Icon

Dashboard link:

## Problem Statement
The organization faced challenges in:
- Identifying inactive employees still on the payroll.
- Understanding the demographic distribution across departments and job levels.
- Tracking workforce engagement and identifying employees nearing retirement age.
- Simplifying access to individual employee data for quick HR actions.

## New Skills Demonstrated
The following Excel features were incorporated:

-	Search Bar by simply typing the employee name.
-	Button to enhance interativity.

## Data Sourcing

The data used was collected from Bash Logistics, It's made up of 1 csv files. Imported the files into Excel for analysis and Visualization. 

## Steps Followed

### Step 1: Load the Data
Import data into Excel from the desktop, a csv files.

### Step 2: Data Transformation/Cleaning

Data was efficiently cleaned and transformed with Power query Editor of Excel.

- Power Querry Editor automatically cleaned the data type.
- Manually Standardized column names for clarity (e.g., “Employee_Status,” “Job_Level,” “Department”). 
- Transform the csv file as needed to ensure it is in the appropriate usage by creating new calculated column such as:

     Classified employees into “In_Service” and “Retrenched” groups, using the below formula -

            **= Table.AddColumn(#"Age_range changed", "Employee_review", each if [Age_range] = "Above 63" then "Retrenched" else "In_service")**

     Created an age group segmentation (20–30, 31–41, 42–52, 53–63, and Above 63), using the below formula - 

            **= Table.AddColumn(#"Changed Type", "Age_range",
                  each if [Age] <= 30 then "20 - 30"
                  else if [Age] <= 41 then "31 - 41"
                  else if [Age] <= 52 then "42 - 52"
                  else if [Age] <= 63 then "53 - 63"
                  else "Above 63")**

  IMAGE -
  
### Step 3: Data Modelling

Loaded and modeled the dataset in Excel Power Query. 
Querry depended on a workbook
Defined relationships between key HR fields for interactive filtering.

IMAGE - QUERRY DEPENDENCY

### Step 4: Analytics Visualization

1. Utilized Pivot Tables to analyze Key Performace Indicators (KPI) to facilitate swift insights.
2. Leverage OFFSET functions within selected Pivot Tables, to enable to visualize certain charts.
           ** =INDEX(departments, 0,0)**
3. The Pivot Tables comprises 12 reports:

| Pivot Tables                        | Pivot Tables                                    |
| ------                              | :----                                           |
| Total Employee                      |    Employee by Location and Distribution Centre |  
| Gender Ratio                        |    Employee by Department and Designation       |
| Employee Status Segmentation        |    Job Level of Employee                        |
| Religion Segmentation               |    Count of Employee by Age Range               |
| Employee Status                     |    Employee Review Segmentation                 |
  
You can interact with the report [here]

4. Steps Taken to Create the Interactive Search Bar in the Dashboard.
     1. Created a Search Input Field

          Designed a dedicated search bar in the dashboard for users to type an employee’s name.

     2. Applied Excel Function to Detect Search Input

          Used the formula below to count when an entry is made in the search field:
                              ** =COUNTA(Dashboard!F3)**

     3. Identified Required Data Columns

          Copied and reviewed column headers from the HRdata sheet to determine the fields needed for the search output.

     4. Built a Pivot Table for Search Data Structure

          Created a Pivot Table and selected only the columns required for the search results.

     5. Re-created Search Headers for Display

          Copied the Pivot Table headers into a new cell range to serve as the structured output layout.

     6. Displayed Search Headers When Input Is Detected

          Used an IF formula to show the selected column header only when a name is entered in the search bar:
                                   ** =IF($B$2=1, L5, "")**

     7. Displayed Employee Details Matching the Search Input

          Used VLOOKUP combined with MATCH to dynamically fetch and display employee details based on the search query:
        
                   ** =IFERROR(VLOOKUP(Dashboard!$F$3, searchrange, MATCH(N6, $C$5:$L$5, 0), 0), "")**

     9. Created Dashboard Status Indicators

          Used simple logic checks to verify whether values exist before showing results:

                                  ** =IF(N6="",0,"yes")

                                   =IF(N7="",0,"yes")**

     10. Compared Status Values for Validation

          Added a comparison formula to check whether employee details exist:
                                   ** =O10=O11 **

     11. Displayed Error Message if No Record is Found

          Provided user-friendly feedback for invalid or unmatched search entries:
                    ** =IF(O12=TRUE, "", "Employee records not found, retry")**
 
5. A switched button was created to quickly move from Analysis to Dashboard to Cleaned data and Vice Versa.

## Final dashboard and other Necessary Visuals.

The final HR Dashboard provides a clear, interactive visualization of the organization’s workforce. It highlights employee status, demographics, departmental structure, and job-level distribution, while offering instant access to individual employee details through the interactive search feature.

### Key Facts & Figures Identified 

- The organization has 151 employees, with 141 active and 10 inactive staff requiring payroll review.

- The workforce is 78% male and 22% female, showing a significant gender imbalance.

- 60% of employees are married, while singles and divorced staff make up 38% and 3% respectively.

- A majority of employees identify as Muslim (93), followed by Christian (29) and Hindu (17).

- Job levels are dominated by Officers (71) and Staff (63), with only a few senior executives and top-level leaders.

- 16% of employees are nearing retirement age, indicating an urgent need for succession planning.

 ## Conclusion & Recommendation
 
The HR Analytics Dashboard effectively addresses the organization’s HR challenges by providing a complete overview of workforce composition and employee status. With dynamic insights and real-time employee lookup, the dashboard strengthens HR decision-making and supports effective resource planning.

Based on insights generated:

1. Workforce Retirement Planning

16% of employees are close to retirement. Succession planning and recruitment activities should begin immediately.

2. Payroll Optimization

10 inactive employees should be reviewed and potentially removed from payroll to reduce overhead costs.

3. Improve Gender Balance

The workforce is predominantly male; HR should prioritize gender diversity in future hiring cycles.

4. Departmental Realignment

Some departments are overloaded while others are light. Workload redistribution or recruitment may be required.

5. Employee Engagement Strategy

Introduce employee satisfaction surveys and performance metrics to identify disengagement early.

6. Expand HR Reporting Automation

Future upgrades could include:

Automatic monthly data refresh

HRMS integration

Predictive analytics for turnover and workforce planning.

Thank You.





            







