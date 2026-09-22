# Data-Cleaning-Visualization

## 📌 Project Overview

This project focuses on cleaning, preprocessing, analyzing, and visualizing an employee dataset using Python.

The project demonstrates common data-cleaning techniques such as handling missing values, removing duplicate records, detecting salary outliers, converting data types, cleaning text fields, and generating visualizations for better understanding of the dataset.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data loading, cleaning, manipulation, and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical data visualization
* **Jupyter Notebook**
* **Excel** – Input and cleaned output datasets

---

## 📂 Project Files

| File                                | Description                                                                 |
| ----------------------------------- | --------------------------------------------------------------------------- |
| `sample_data_cleaning_project.xlsx` | Original employee dataset containing missing values and duplicate records   |
| `Data_Cleaning_Project.ipynb`       | Jupyter Notebook containing the complete data-cleaning and analysis process |
| `cleaned_employee_data.xlsx`        | Final cleaned employee dataset                                              |

---

## 📊 Dataset

The dataset contains employee information with the following columns:

* **Name** – Employee name
* **Age** – Employee age
* **Salary** – Employee salary
* **Join_Date** – Employee joining date
* **Department** – Employee department

The original dataset contains **43 rows and 5 columns**.

---

## 🧹 Data Cleaning Process

The following steps were performed in the project:

### 1. Load the Dataset

The original Excel file was loaded using Pandas.

```python
df = pd.read_excel("sample_data_cleaning_project.xlsx")
```

### 2. Inspect the Dataset

The dataset was examined using functions such as:

* `head()`
* `shape`
* `info()`
* `columns`
* `describe()`

### 3. Check Missing Values

Missing values were identified using:

```python
df.isnull().sum()
```

Missing values were found in the **Age** and **Salary** columns.

### 4. Remove Duplicate Records

Duplicate rows were identified and removed:

```python
df = df.drop_duplicates()
```

### 5. Handle Missing Age Values

Missing values in the `Age` column were replaced using the median age:

```python
df['Age'] = df['Age'].fillna(df['Age'].median())
```

### 6. Handle Missing Salary Values

Missing salary values were replaced using the median salary:

```python
df['Salary'] = df['Salary'].fillna(df['Salary'].median())
```

### 7. Detect Salary Outliers

The Interquartile Range (IQR) method was used to identify potential salary outliers.

```python
Q1 = df['Salary'].quantile(0.25)
Q3 = df['Salary'].quantile(0.75)

IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
```

A new column called `Salary_Outlier` was created to identify potential outlier records.

### 8. Convert Date Data

The `Join_Date` column was converted into a proper datetime format:

```python
df['Join_Date'] = pd.to_datetime(df['Join_Date'])
```

### 9. Clean Text Data

Extra spaces were removed from the `Name` and `Department` columns:

```python
df['Name'] = df['Name'].str.strip()
df['Department'] = df['Department'].str.strip()
```

### 10. Final Validation

The cleaned dataset was checked again for:

* Missing values
* Duplicate rows
* Number of rows and columns
* Potential salary outliers
* Correct data types

---

## 📈 Data Visualization

The project includes several visualizations using Matplotlib and Seaborn.

### Employee Count by Department

A count plot was created to visualize the number of employees in each department.

### Salary Distribution

A histogram with KDE was used to understand the distribution of employee salaries.

### Age Distribution

A histogram with KDE was used to visualize the distribution of employee ages.

### Salary Boxplot

A boxplot was created to visually identify potential salary outliers.

---

## 💾 Output

After cleaning and processing the data, the final dataset was exported as an Excel file:

```python
df.to_excel("cleaned_employee_data.xlsx", index=False)
```

The cleaned dataset contains **42 rows and 6 columns**, including the additional `Salary_Outlier` column.

The cleaned data was also exported to CSV format.

---

## 🎯 Key Objectives

The main objectives of this project were:

* Understand the structure of an employee dataset
* Identify and handle missing data
* Remove duplicate records
* Detect potential outliers
* Convert columns to appropriate data types
* Clean textual data
* Perform basic employee data analysis
* Create meaningful data visualizations
* Export the cleaned dataset for further use

---

## 🔍 Final Result

The project successfully transformed the original employee dataset into a cleaner and more structured dataset that can be used for further analysis.

The final dataset has:

* **42 employee records**
* **6 columns**
* **No missing values**
* **No duplicate rows**
* **Salary outlier identification**
* **Proper date formatting**
* **Cleaned text fields**

---

## 👩‍💻 Project Workflow

```text
Original Excel Dataset
        ↓
Load Data using Pandas
        ↓
Inspect Dataset
        ↓
Check Missing Values
        ↓
Remove Duplicates
        ↓
Handle Missing Age & Salary
        ↓
Detect Salary Outliers
        ↓
Convert Date Format
        ↓
Clean Text Fields
        ↓
Validate Cleaned Dataset
        ↓
Visualize Data
        ↓
Export Cleaned Dataset
```

---

## 🚀 Future Improvements

The project can be extended by adding:

* Department-wise salary analysis
* Average salary calculations
* Employee joining-year analysis
* Interactive dashboards
* More advanced statistical analysis
* Additional outlier detection techniques
* Machine learning-based employee analytics

---

## 📌 Conclusion

This project provides a practical demonstration of the fundamental steps involved in **data cleaning and exploratory data analysis using Python**. It shows how raw employee data can be processed, cleaned, analyzed, visualized, and exported into a usable format.
