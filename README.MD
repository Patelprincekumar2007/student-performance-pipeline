# Student Performance Data Pipeline

## Project Overview
A beginner-friendly data engineering project built using Databricks, PySpark, Delta Lake, and SQL. It processes student performance data, checks data quality, removes missing records and duplicate student IDs, and analyzes academic performance by department.

## Technologies Used
- Databricks
- Python
- PySpark
- Delta Lake
- SQL
- Git and GitHub

## Pipeline Workflow
1. Load student data from a source table.
2. Inspect the data schema.
3. Check for missing values and duplicate student IDs.
4. Clean the dataset.
5. Save cleaned data as a Delta table.
6. Analyze student counts and average marks by department.
7. Verify pipeline statistics.

## Data Quality Results
- Original records: 1,000
- Cleaned records: 1,000
- Removed records: 0

## Output Table
`student_performance_cleaned`

## Note
The dataset contains synthetic student records created for educational purposes. It does not contain verified real student information.