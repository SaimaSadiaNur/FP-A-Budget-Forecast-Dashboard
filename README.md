# FP-A-Budget-Forecast-Dashboard
An Excel-based financial planning and analysis system that transforms financial budget, expense, and revenue data into an interactive management dashboard using Power Query, Power Pivot, DAX, and Excel.

The project demonstrates an end-to-end FP&A workflow covering budget vs. actual analysis, revenue forecasting, expense variance analysis, forecast accuracy, data transformation, financial validation, and interactive reporting.

# What It Does
1. Imports financial data into Excel.
2. Cleans and transforms the dataset using Power Query.
3. Builds a relational star-schema data model using Power Pivot.
4. Creates analytical measures using DAX.
5. Analyzes budget utilization, actual spending, revenue performance, and forecast accuracy.
6. Presents the results through an interactive executive dashboard.
7. Enables management-level analysis through department, fiscal quarter, and expense-category filters.

The result is a structured FP&A reporting workflow that turns raw financial records into an interactive management reporting tool.

# Business Questions Addressed

The dashboard is designed to answer questions such as:

How much of the allocated budget has been utilized?
Which departments are spending above or below budget?
How does actual revenue compare with the forecast?
How accurate is the revenue forecast?
Which departments have the largest expense variances?
How does financial performance change across fiscal quarters?
How does performance change when filtering by department or expense category?

# Data
The project uses a structured financial dataset containing budget, expense, and revenue information across departments and fiscal quarters.
The core fields used in the analytical model include:
| Field              | Description                                       |
| ------------------ | ------------------------------------------------- |
| `Record_ID`        | Unique financial record identifier                |
| `Fiscal_Quarter`   | Fiscal quarter associated with the record         |
| `Department`       | Department responsible for the financial activity |
| `Expense_Category` | Expense classification                            |
| `Budget_Allocated` | Budget originally allocated                       |
| `Budget_Utilized`  | Budget utilization recorded in the source         |
| `Monthly_Expense`  | Recorded expense amount                           |
| `Revenue_Forecast` | Forecasted revenue                                |
| `Actual_Revenue`   | Actual revenue                                    |

Raw data is kept separate from the analytical model so that transformations can be reproduced through Power Query rather than manually modifying the source data.

# Data Transformation & Modeling

The project follows a layered approach:

┌─────────────────────┐
│     Raw Financial   │
│        Dataset      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    Power Query      │
│ Clean + Transform   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────────────┐
│       Power Pivot           │
│     Star Schema Model       │
└──────────┬──────────────────┘
           │
           ▼
┌─────────────────────────────┐
│       DAX Measures          │
│ Budget | Expense | Revenue  │
└──────────┬──────────────────┘
           │
           ▼
┌─────────────────────────────┐
│     Executive Dashboard     │
│ KPIs + Charts + Slicers     │
└─────────────────────────────┘
           │
           ▼
┌─────────────────────────────┐
│       VBA Macros
│   Refresh + Recalculation
└─────────────────────────────┘
# Data Model
The model uses a star-schema structure consisting of:
1. FactFinancial — financial transactions and numeric measures
2. DimDate — fiscal quarter dimension
3. DimDepartment — department dimension
4. DimExpenseCategory — expense category dimension

The fact table contains the numerical financial data while descriptive attributes are maintained in dimension tables.
This structure allows DAX measures to respond dynamically to dashboard filters and provides a scalable foundation for additional financial analysis.

# DAX Analysis
The dashboard uses DAX measures rather than hard-coded calculations in the source data.
# Expense Analysis
Total Budget
Total Actual Spend
Expense Variance
Expense Variance %
Budget Utilization %
# Revenue Analysis
Revenue Forecast
Actual Revenue
Revenue Variance
Revenue Variance %
Forecast Accuracy %
The measures are designed to recalculate dynamically according to the selected department, fiscal quarter, and expense category.

DAX measures used in the project are documented in:
src/DAX.txt

# Dashboard
The final dashboard focuses on the financial metrics most relevant to management rather than displaying a large number of basic statistics.
# KPI Cards
The dashboard includes:
1. Total Budget
2. Forecast Accuracy %
3. Total Revenue
4. Actual Expense
5. Expense Variance %
6. Revenue Variance %
# Visual Analysis
The dashboard includes:
1. Budget vs Actual Expense by Department
2. Revenue Forecast vs Actual by Fiscal Quarter
3. Expense Variance by Department
# Interactive Filters
Users can filter the dashboard by:
1. Fiscal Quarter
2. Department
3. Expense Category
All dashboard components are connected to the underlying Power Pivot data model, allowing the KPIs and visualizations to respond dynamically to selections.

Project Structure
FP-A-Budget-Forecast-Dashboard/
│
├── README.md
│
├── data/
│   └── sample_financial_data.csv
│
├── workbook/
│   └── FP&A_Budget_Forecast_Dashboard.xlsm
│
├── docs/
│   └── dashboard_preview.png
│
└── src/
    └── DAX.txt
    └── VBA.txt

# Tech Stack
Microsoft Excel — financial analysis and dashboard
Power Query — data cleaning, transformation, and ETL
Power Pivot — relational data model and star-schema architecture
DAX — analytical measures and financial KPIs
Excel PivotTables & Charts — interactive visualization
Excel Slicers — dashboard filtering
Excel Macros - dashboard automation
# Dashboard Preview
The dashboard provides a management-level view of:
<img width="916" height="359" alt="dashboard_preview" src="https://github.com/user-attachments/assets/0dd2ceaa-d671-4e85-bf2d-94ddc6b90246" />
# How to Use
Download the Excel workbook from the workbook/ folder.
Open the workbook in Microsoft Excel.
Ensure Power Query and Power Pivot are available.
Refresh the queries/model when new source data is available.
Use the dashboard slicers to analyze performance by:
Department
Fiscal Quarter
Expense Category
The dashboard is designed to update its calculations automatically when the underlying model is refreshed.
# Project Objective
This project was developed as a practical demonstration of an FP&A reporting workflow in Excel, with an emphasis on moving beyond basic spreadsheet reporting toward a structured analytical model.
The objective was to combine:
Data preparation → Financial modeling → Variance analysis → Forecast analysis → Interactive reporting
within a single Excel-based solution.
# Roadmap
Potential future enhancements include:
Add automated report export to PDF
Add monthly time-series forecasting when monthly data becomes available
Add scenario analysis for budget assumptions
Add budget reforecasting functionality
Add automated email/report distribution
Expand financial validation and exception reporting
