# Netflix Power BI Data Analytics Project

## Project Overview

This project was completed as part of the **Auspify Data Analytics Internship**.

The project focuses on analyzing Netflix content using **Microsoft Power BI**, including data cleaning, data modeling, dashboard development, geographic analysis, and content growth trends.

All four tasks are included in one Power BI `.pbix` file using separate report pages.

---

## Project Objectives

- Clean and prepare the Netflix dataset
- Build a reliable Power BI data model
- Create interactive dashboards
- Analyze Movies and TV Shows
- Study country-wise content distribution
- Analyze content growth over time
- Use DAX measures for KPIs and trend analysis
- Build interactive slicers and filters
- Present insights in a professional dashboard format

---

## Tools & Technologies

- Microsoft Power BI Desktop
- Power Query
- DAX
- Data Modeling
- Shape Map / GeoJSON
- CSV Dataset
- GitHub

---

# Task 1 - Data Preparation & Modeling

## Objective

Prepare the Netflix dataset for analysis and create a basic data model.

## Work Completed

- Imported the Netflix dataset into Power BI
- Used Power Query for data cleaning
- Checked column quality, distribution, and profile
- Corrected data types
- Replaced placeholder values such as `Not Given` with null values
- Investigated and fixed data errors
- Checked duplicate records
- Validated `show_id` uniqueness
- Checked consistency of fields such as Type, Rating, Duration, Country, and Director
- Created a Date Table
- Created relationships in Model View
- Added basic DAX measures for validation

## Main Model Components

- `Dataset`
- `DateTable`
- `CountryContent`

---

# Task 2 - Netflix Content Overview Dashboard

## Objective

Create an interactive dashboard showing the overall distribution of Netflix content.

## Key KPIs

- Total Titles
- Total Movies
- Total TV Shows
- Total Countries

## Visuals Created

- Movies vs TV Shows Donut Chart
- Titles by Release Year
- Top 10 Countries by Titles
- Top 10 Directors by Titles
- Type Slicer
- Release Year Slicer

## Key Results

- **Total Titles:** 8,790
- **Total Movies:** 6,126
- **Total TV Shows:** 2,664
- **Countries Covered:** 85

---

# Task 3 - Global Content Insights Dashboard

## Objective

Analyze Netflix content distribution across countries and regions.

## Data Preparation

A separate `CountryContent` query was created for geographic analysis.

The country field was:

- Split into separate rows for multi-country records
- Trimmed to remove extra spaces
- Filtered to remove null country values
- Categorized as `Country/Region`

A custom world GeoJSON file was used for the Shape Map.

## DAX Measure

```DAX
Country Titles =
DISTINCTCOUNT('CountryContent'[show_id])
```

## Visuals Created

- World Shape Map
- Top 10 Countries by Content Volume
- Type Slicer
- Release Year Slicer
- Countries Covered KPI

---

# Task 4 - Content Growth & Trend Analysis

## Objective

Analyze Netflix content growth and release-year trends over time.

## DAX Measures

### Total Titles Numeric

```DAX
Total Titles Numeric =
COUNTROWS('Dataset')
```

### Previous Year Titles

```DAX
Previous Year Titles =
VAR CurrentYear =
    SELECTEDVALUE('Dataset'[release_year])
RETURN
    CALCULATE(
        [Total Titles Numeric],
        FILTER(
            ALL('Dataset'[release_year]),
            'Dataset'[release_year] = CurrentYear - 1
        )
    )
```

### Year-over-Year Growth

```DAX
YoY Growth % =
DIVIDE(
    [Total Titles Numeric] - [Previous Year Titles],
    [Previous Year Titles]
)
```

### Growth Status

```DAX
Growth Status =
IF(
    [Latest Year Growth] >= 0,
    "Growth",
    "Decline"
)
```

## Visuals Created

- Total Titles by Release Year
- Year-over-Year Content Growth
- Movies vs TV Shows Growth Trend
- Latest Year Growth KPI
- Growth Status KPI
- Type Slicer
- Release Year Range Slicer

## Latest Growth Result

- **Latest Year Growth:** -37.88%
- **Growth Status:** Decline

> The latest-year decline reflects the records available in this dataset and should not automatically be interpreted as Netflix business performance.

---

# Dashboard Pages

The final Power BI file contains separate pages for each task:

1. Task 1 - Data Modeling
2. Task 2 - Netflix Dashboard
3. Task 3 - Global Content Insights
4. Task 4 - Content Growth & Trend Analysis

---

# Repository Structure

```text
Netflix_PowerBI_Project/
│
├── Netflix_PowerBI_Final.pbix
├── Dataset.csv
├── README.md
│
└── Screenshots/
    ├── Task1_Data_Preparation.png
    ├── Task1_Data_Model.png
    ├── Task2_Content_Overview.png
    ├── Task3_Global_Content_Insights.png
    └── Task4_Growth_Trend_Analysis.png
```

---

# Screenshots

- `Screenshots/Task1_Data_Preparation.png`
- `Screenshots/Task1_Data_Model.png`
- `Screenshots/Task2_Content_Overview.png`
- `Screenshots/Task3_Global_Content_Insights.png`
- `Screenshots/Task4_Growth_Trend_Analysis.png`

---

# Key Skills Demonstrated

- Data Cleaning
- Power Query
- Data Transformation
- Data Validation
- Data Modeling
- DAX Measures
- KPI Development
- Data Visualization
- Dashboard Design
- Geographic Analysis
- Time-Series Analysis
- Year-over-Year Growth Analysis
- Interactive Filtering
- Business Intelligence

---

# How to Use the Project

1. Download or clone this repository.
2. Open `Netflix_PowerBI_Final.pbix` using Microsoft Power BI Desktop.
3. Navigate through the report pages.
4. Use the slicers to interact with the dashboards.
5. Review the Power Query steps, DAX measures, and model relationships for implementation details.

---

# Project Status

**Completed**

All four internship tasks have been completed and included in the final Power BI project.

---

## Author

**Zohaib Hassan**  
Email: **zohaibhassanpk2@gmail.com**  
Data Analytics / Power BI Project
