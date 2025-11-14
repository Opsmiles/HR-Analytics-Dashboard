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

### Step 5: Analytics Visualization

1. Utilized Pivot Tables to analyze Key Performace Indicators (KPI) to facilitate swift insights.
2. Leverage OFFSET functions within selected Pivot Tables, to enable to visualize certain charts.
           ** =INDEX(departments, 0,0)**
3. The report comprises 12 reports: 
- Total Employee                      |      - Employee by Location and Distribution Centre
- Gender Ratio                        |      - Employee by Department and Designation
- Employee Status Segmentation        |      - Job Level of Employee
- Religion Segmentation               |      - Count of Employee by Age Range
- Employee Status                     |      - Employee Review Segmentation
  
You can interact with the report [here]
4. Use Excel Funtions to create interactive Search button Funtion in the Dashoard.

- Count if an entry is in the search bar at the dashboard using this formular
            ** =COUNTA(dashboard!F3)**
- Copy and paste the headings in the HRdata Sheet to Know the columns needed for the search
- Use Pivot Table to input the colummns needed for the search
- Copy and Paste the Column headers from the Pivot Table into another cells
- Write a formular to show the Pivot Table Header if Entry is made in the Dashboard search bar
            ** =IF($B$2=1, L5, "")**
- Write Excel funtion to show the details of the name entry in the dashboard search bar
            ** =IFERROR(VLOOKUP(dashboard!$F$3,searchrange,MATCH(N6,$C$5:$L$5, 0), 0), "")**
- Dashboard Statement                      |    - Employee Information
            ** =IF(N6="", 0, "yes")**      |            ** =IF(N7="",0, "yes")**
- Compare                                  |    - Display
            ** =O10=O11**                  |            ** =IF(O12=TRUE, "", "Employee records not found, retry")**
5. A switched button was created to quickly move from Analysis to Dashboard to Cleaned data and Vice Versa.

## Final dashboard and other Necessary Visuals.





            






            







