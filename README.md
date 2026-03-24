# Customer Sales Data ETL (Alteryx)

🎯 **Project Goal**: Build an ETL workflow that cleans sales data and prepares it for Power BI/Tableau visualization.

## 📊 Dataset Overview
This project uses three source files to simulate a real-world sales environment:
- **Orders.csv**: Transactional data (OrderID, CustomerID, Region, Sales, Date).
- **Customers.csv**: Customer details (CustomerID, CustomerName, Segment).
- **Regions.csv**: Geographical mapping (Region, Manager).

## 🔧 Alteryx Workflow Steps

### Step 1: Input Data
Load the three source CSV files into the Alteryx canvas.

### Step 2: Joins
- **Join #1**: Connect `Orders` and `Customers` on `CustomerID`.
- **Join #2**: Connect the resulting stream with `Regions` on `Region`.

### Step 3: Select Tool
Filter and reorder columns to keep only relevant fields:
- `OrderID`
- `CustomerName`
- `Segment`
- `Region`
- `Manager`
- `Sales`

### Step 4: Formula Tool
Create a new field `Revenue_Category` to segment performance:
```sql
IF [Sales] > 1200 THEN "High"
ELSEIF [Sales] > 800 THEN "Medium"
ELSE "Low"
ENDIF
```

### Step 5: Data Cleansing
Apply the Data Cleansing tool to:
- Remove Nulls
- Trim whitespace from all string fields
- Remove special characters

### Step 6: Output
Save the final processed dataset as `Cleaned_Sales_Data.xlsx` or `Cleaned_Sales_Data.csv`.

---
*Created by [HarshalGupta3011](https://github.com/HarshalGupta3011)*
