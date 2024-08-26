# Performance-Analysis of Plant Co. for 2023-2024

The primary goal of this dashboard is to identify the challenges faced by Plant Co. and highlight opportunities for improvement.

## You can interact with the Dashboard!

<iframe title="Portofolio_Performance_Report" width="1024" height="612" src="https://app.powerbi.com/view?r=eyJrIjoiZDUwNmZhYzMtZjA3OS00YjFjLWE4MDYtNWQ3OTJmNTQyYjEyIiwidCI6ImViOGZiNTVjLTcyMDEtNDE0Yy05MDdlLWVhYTAwMmZlOThhMCIsImMiOjN9" frameborder="0" allowFullScreen="true"></iframe>


## 📚 About Data

The data set consists of three tables: plant_fact, accounts, and Plant_Hierarchy. Each table contains specific columns that provide detailed information about products, sales, and accounts.

The dataset is composed of three tables: the plant_fact table has 2723 rows, the accounts table has 1745 rows and the plant_hierarchy has 1001 rows.

## ✏️ Data Wrangling

Conducted simple data wrangling and data cleaning:
- Renamed some of the columns and tables
- Removed duplicates from the unique identifiers
- Cast date_time as date 

📍 Clean Data: [plant_dataset.xls](assets/Plant_DTS.xls)

## DAX Measures

This DAX function changes the title of the chart vizualization based on the selected value. There are similar functions for the report title, scatter plot, and waterfall vizuals.

```
_Column Chart title = SELECTEDVALUE(Slc_Values[Values]) & " YTD & PYTD | Month" 
```


This DAX function S_PYTD is designed to return a measure based on the selected value from a slicer.

```
S_PYTD = 
VAR selected_value = SELECTEDVALUE(Slc_Values[Values])
VAR result = SWITCH(selected_value,
    "Sales", [PYTD_Sales],
    "Quantity", [PYTD_Quantity],
    "Gross Profit", [PYTD_GrossProfit],
    BLANK()
)
RETURN
result
```

This DAX function is used to calculate the PriorYearToDate values of the Gross Profit. There are similar calculations for the Quantity and Sales dimensions.

```
PYTD_GrossProfit = 
CALCULATE(
    [Gross Profit],
    SAMEPERIODLASTYEAR(Dim_Date[Date]),
    Dim_Date[Inpast] = TRUE
)
```










