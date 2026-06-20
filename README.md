# 🏅 OlympusX – End-to-End Azure Data Engineering Pipeline

An end-to-end Azure Data Engineering project that automates the ingestion, transformation, and storage of Olympic datasets using Azure services and Databricks.

> **Project Type:** Data Engineering Portfolio Project  
> **Author:** Gaurav Thombal

---

# 📌 Project Overview

OlympusX is an Azure-based ETL pipeline designed to ingest Olympic datasets from GitHub, store them in Azure Data Lake Storage, transform the data using Databricks SQL, and generate optimized Parquet files for analytics.

This project demonstrates modern data engineering concepts including:

- ETL Pipeline
- Data Lake Architecture
- Bronze → Silver Layer
- Databricks SQL Transformations
- Azure Data Factory
- Delta Tables
- Parquet Format

---

# 🏗️ Architecture

```

GitHub Repository
│
▼
Azure Data Factory
│
▼
Azure Data Lake Storage Gen2
(Bronze Layer)
raw-data/
│
▼
Databricks Free Edition
│
├── SQL Transformations
├── Data Cleaning
├── Data Validation
└── Delta Tables
│
▼
Parquet Files
(Silver Layer)

```

---

# 🛠️ Tech Stack

| Technology | Purpose |
|------------|----------|
| Azure Data Factory | Data Ingestion |
| Azure Data Lake Storage Gen2 | Data Storage |
| Databricks SQL | Data Transformation |
| PySpark | CSV Ingestion |
| Delta Lake | Processed Tables |
| Parquet | Optimized Storage |
| GitHub | Source Data |

---

# 📂 Project Structure

```

OlympusX/

│

├── datasets/

│ ├── athletes.csv

│ ├── coaches.csv

│ ├── entriesgender.csv

│ ├── medals.csv

│ └── teams.csv

│

├── notebooks/

│ ├── olympic-data-transformation.sql

│ └── ingestion.py

│

├── adf/

│ ├── pipeline.json

│ └── datasets/

│

├── screenshots/

│

├── README.md

```

---

# 📁 Dataset

The project contains five Olympic datasets.

| Dataset | Description |
|----------|-------------|
| Athletes | Athlete Information |
| Coaches | Coach Details |
| EntriesGender | Male/Female Participation |
| Medals | Medal Count |
| Teams | Team Information |

---

# 🚀 Pipeline Workflow

## Step 1

Data is stored in a GitHub repository.

↓

## Step 2

Azure Data Factory copies CSV files into Azure Data Lake Storage.

```

GitHub

↓

ADLS

raw-data/

```

↓

## Step 3

CSV files are uploaded into Databricks Volume.

↓

## Step 4

PySpark reads CSV files with headers.

```python
df = spark.read.option("header","true").csv(...)
```

↓

## Step 5

Temporary Views are created.

```
athletes_raw
coaches_raw
entriesgender_raw
medals_raw
teams_raw
```

↓

## Step 6

SQL transformations are applied.

Example:

```sql
SELECT DISTINCT
INITCAP(TRIM(PersonName)) AS PersonName,
TRIM(Country) AS Country,
TRIM(Discipline) AS Discipline
FROM athletes_raw;
```

↓

## Step 7

Delta tables are created.

```
athletes_clean
coaches_clean
entriesgender_clean
medals_clean
teams_clean
```

↓

## Step 8

Processed tables are exported as Parquet files.

---

# ✨ Data Transformations

### Athletes

- Removed Null Values
- Removed Duplicates
- Trimmed Whitespaces
- Standardized Names

---

### Coaches

- Removed Duplicates
- Filled Missing Events
- Trimmed Values

---

### EntriesGender

- Converted Numeric Columns
- Removed Invalid Records

---

### Medals

- Cast Numeric Columns
- Standardized Country Names

---

### Teams

- Removed Duplicate Teams
- Filled Missing Events

---

# 📊 Data Layers

## 🟤 Bronze Layer

Raw CSV files copied from GitHub.

```
raw-data/

athletes.csv

coaches.csv

entriesgender.csv

medals.csv

teams.csv

```

---

## ⚪ Silver Layer

Processed Parquet files.

```

transformed/

athletes/

coaches/

entriesgender/

medals/

teams/

```

---

# 📸 Screenshots

Include screenshots of:

- Azure Data Factory Pipeline
- Azure Data Lake Storage
- Databricks Notebook
- SQL Transformations
- Delta Tables
- Parquet Output

---

# 💡 Key Features

- End-to-End ETL Pipeline
- Azure Data Factory Integration
- Data Lake Architecture
- SQL-Based Data Transformation
- Delta Lake
- Parquet Storage
- Modular Design
- Production-style Folder Structure

---

# 📈 Learning Outcomes

Through this project I learned:

- Azure Data Factory Pipelines
- Azure Data Lake Storage Gen2
- Databricks SQL
- PySpark Data Ingestion
- Delta Lake
- Parquet Optimization
- ETL Pipeline Design
- Data Cleaning
- SQL Transformations

---

# ⚠️ Note

This project was developed using **Databricks Free Edition**.

Due to Free Edition limitations, Azure Data Lake Storage could not be mounted directly inside Databricks. Therefore:

- Data ingestion into ADLS was automated using Azure Data Factory.
- SQL transformations were performed in Databricks.
- Processed data was exported as Parquet files from Databricks.

In a production environment using Azure Databricks, the pipeline can be fully automated by reading from and writing directly to Azure Data Lake Storage using managed identities and Unity Catalog external locations.

---

# 📚 Future Enhancements

- Azure Databricks Workspace
- Unity Catalog
- Direct ADLS Integration
- Azure Synapse Analytics
- Power BI Dashboard
- CI/CD using Azure DevOps
- Incremental Data Loading
- Delta Live Tables

---

# 👨‍💻 Author

**Gaurav Thombal**

Engineering Student | Aspiring Data Engineer

### Skills

- SQL
- Python
- PySpark
- Azure Data Factory
- Azure Data Lake Storage
- Databricks
- Delta Lake
- Power BI

---

⭐ If you found this project helpful, consider giving it a **Star**.
