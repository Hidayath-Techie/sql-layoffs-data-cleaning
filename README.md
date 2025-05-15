# sql-layoffs-data-cleaning

# 🧹 SQL Data Cleaning Project: Layoffs 2022

This project showcases a full data cleaning process using **pure SQL**. The dataset was downloaded from [Kaggle - Layoffs 2022](https://www.kaggle.com/datasets/swaptr/layoffs-2022).

## 📁 Dataset Info

- **Source:** Kaggle (Layoffs 2022)
- **File Name:** layoffs.csv
- **Rows:** 2,333
- **Columns:** 10
- **Focus:** Company layoffs during economic slowdown

## 🧼 Cleaning Steps

### 1. Create Staging Table
- Created `layoffs_staging` to preserve raw data
- All cleaning operations done on a copy

### 2. Removed Duplicates
- Used `ROW_NUMBER()` with `PARTITION BY` to find duplicates
- Kept legit entries (e.g., repeated layoffs for same company)
- Deleted exact duplicate rows

### 3. Standardized Data
- Converted date string to proper `DATE` type
- Cleaned inconsistent values like:
  - `CryptoCurrency`, `Crypto Currency` → `Crypto`
  - `United States.` → `United States`
- Trimmed extra spaces and symbols

### 4. Handled Nulls
- Replaced empty `industry` values using self `JOIN` on company
- Set blank `industry` strings to `NULL` for easier handling

### 5. Removed Useless Data
- Deleted rows where both `total_laid_off` and `percentage_laid_off` were NULL
- Dropped helper columns (like `row_num`) after use

## ✅ Final Output

Cleaned table: `layoffs_staging2`

- No duplicates  
- Standardized values  
- Proper date format  
- Nulls handled logically  

## 🔧 Tools Used

- SQL (MySQL syntax)
- Functions: `ROW_NUMBER()`, `STR_TO_DATE()`, `JOIN`, `UPDATE`, `DELETE`

## 📊 Ready For

- EDA (Exploratory Data Analysis)
- Dashboarding (Power BI, Tableau)
- Further modeling (Python, R)

## 📌 Notes

All cleaning was done using SQL only — no external tools or languages. This approach proves that SQL alone can handle powerful data cleaning tasks for real-world datasets.
