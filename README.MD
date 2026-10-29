# Student Performance Data Pipeline

A data engineering project built using **Databricks, PySpark, Delta Lake, and SQL** to clean, validate, transform, and analyze student performance data.

## Project Overview

This project demonstrates a basic end-to-end data pipeline using a synthetic dataset of 1,000 student records. It analyzes academic performance, attendance, backlogs, and placement status.

## Objectives

- Load student data into Databricks.
- Inspect the dataset and identify data quality issues.
- Clean missing values and duplicate student records.
- Create a pass-status column based on marks.
- Validate marks, attendance, and backlog values.
- Analyze student performance by department.
- Store the processed data in Delta tables.
- Perform analysis using PySpark and SQL.

## Tech Stack

- **Databricks** — Data processing environment
- **Apache Spark / PySpark** — Data transformation and analysis
- **Delta Lake** — Processed data storage
- **SQL** — Data analysis and aggregation
- **Python** — Pipeline logic
- **Git and GitHub** — Version control

## Dataset

The project uses a synthetic dataset containing 1,000 student records.

| Column | Description |
|---|---|
| `student_id` | Unique student identifier |
| `student_name` | Student name |
| `department` | Academic department |
| `semester` | Current semester |
| `marks` | Student marks |
| `attendance_percentage` | Attendance percentage |
| `backlogs` | Number of backlogs |
| `fees_paid` | Fee payment status |
| `placement_status` | Placement status |

## Pipeline Workflow

1. **Data Loading:** Load the dataset into a Databricks table.
2. **Data Exploration:** Inspect the schema, records, and data quality.
3. **Data Cleaning:** Remove records with missing values and duplicate student IDs.
4. **Data Transformation:** Create the `pass_status` column using a 40-mark threshold.
5. **Data Validation:** Check marks and attendance ranges and identify negative backlog values.
6. **Data Analysis:** Calculate average marks, department-level statistics, pass counts, and placement statistics.
7. **Delta Lake Storage:** Save the processed dataset as a Delta table.

## Key Transformations

### Create pass status

```python
df_clean = df_clean.withColumn(
    "pass_status",
    df_clean.marks >= 40
)
```

### Analyze average marks by department

```python
df_clean.groupBy("department") \
    .avg("marks") \
    .show()
```

### Analyze placement status

```python
df_clean.groupBy(
    "department",
    "placement_status"
).count().show()
```

### Save final data

```python
df_clean.write \
    .format("delta") \
    .mode("overwrite") \
    .saveAsTable("student_performance_final")
```

## Data Quality Checks

- Missing-value inspection
- Duplicate student ID detection
- Marks validation: 0–100
- Attendance validation: 0–100%
- Negative backlog detection

The initial cleaning process reported 1,000 original records, 1,000 cleaned records, and 0 removed records.

## Output

The final Delta table is named:

`student_performance_final`

It contains the processed student data and the derived `pass_status` column, assuming the final notebook changes were saved successfully.

## Repository Structure

```text
student-performance-pipeline/
├── data/
│   └── student_performance.csv
├── notebook/
│   └── student_pipeline.ipynb
├── README.MD
└── .gitignore
```

## How to Use

1. Open your Databricks workspace.
2. Upload the synthetic student dataset.
3. Create or access the source table.
4. Run the notebook cells in order.
5. Review the data quality checks and analysis outputs.
6. Verify the final Delta table in the catalog.

## Skills Demonstrated

- Data ingestion
- Data cleaning and validation
- PySpark DataFrame operations
- SQL aggregations
- Delta Lake table management
- Data quality checks
- Git and GitHub version control

## Future Improvements

- Automate pipeline execution.
- Add visual dashboards for academic performance.
- Build more advanced placement analytics.
- Add scheduled data quality checks.
- Implement pipeline monitoring and error handling.

## Author

**Patel Princekumar**

GitHub: [@Patelprincekumar2007](https://github.com/Patelprincekumar2007)

## Disclaimer

This project uses synthetic data for educational and demonstration purposes. The pass threshold of 40 marks is a practice assumption, not a verified university grading policy.
