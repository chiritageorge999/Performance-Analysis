# Performance-Analysis
Portfolio project

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











