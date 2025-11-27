# 🚀 Olist End-to-End Data Engineering Project (Azure)

## 📍 Overview

This project demonstrates a complete **Modern Data Engineering Pipeline on Azure** using the **Brazilian E-Commerce Olist Dataset**. The pipeline performs:

* **Data ingestion** from multiple sources
* **Data transformation & enrichment**
* **Data storage in Bronze → Silver → Gold layers**
* **Querying using Azure Synapse**
* **Visualization using Power BI / Tableau / Fabric**

---

## 🏗️ Architecture

Below is the high-level architecture of the pipeline:

![Architecture Diagram](assets/arch.png)

---

## 🔧 Tech Stack

| Component       | Service Used               |
| --------------- | -------------------------- |
| Cloud           | Microsoft Azure            |
| ETL / Ingestion | Azure Data Factory         |
| Storage         | Azure Data Lake Gen2       |
| Processing      | Azure Databricks (PySpark) |
| NoSQL Source    | MongoDB Atlas              |
| Warehouse       | Azure Synapse              |
| File Format     | Parquet                    |
| Dashboard       | Power BI / Fabric          |
| Source Control  | GitHub                     |

---

## 📥 Data Ingestion

Ingesting data from:

* GitHub (CSV)
* MySQL / HTTP sources

Pipeline includes **Lookup → ForEach → CopyActivity**.

### Example Pipeline Execution

![ADF Pipeline](assets/adf_pipeline.png)

### Preview of input JSON file in Lookup

![Lookup](assets/lookup_json.png)

---

## 🧹 Data Transformation

Transformation performed using **Azure Databricks / PySpark** including:

* Duplicate and null record removal
* Data type conversions
* Calculated columns for business insights

### Cleaning Function Example

```python
def clean_data(df, name):
    print("Cleaning " + name)
    return df.dropDuplicates().na.drop('all')
```

![Cleaning Code](assets/cleaning_code.png)

### Timestamp Conversion Example

![Timestamp](assets/timestamp_cleaning.png)

---

## 📊 Data Visualization in Databricks

Example visualization of delivery delay grouped by payment type:

![Visualization](assets/delay_viz.png)

---

## 🟢 Enrichment Layer using MongoDB

Reading reference table using PyMongo and joining with transformed layer.

![Mongo](assets/mongo_read.png)

---

## 🪣 Gold Layer & Synapse SQL

Final optimized Parquet tables stored in the Gold Zone and queried using SQL.

```sql
CREATE EXTERNAL TABLE gold.finaltable
WITH (
    LOCATION='finalserving',
    DATA_SOURCE=goldlayer,
    FILE_FORMAT=externalfileformat
)
AS SELECT * FROM gold.final2;
```

![Synapse Query](assets/synapse_query.png)

---

## 📊 Dashboard / Visualization

Business-ready output available for BI tools.

![PowerBI](assets/powerbi.png)

---

## 📂 Repository Structure

```
Olist-Data-Pipeline/
│── notebooks/
│── synapse/
│── adf/
│── assets/      # screenshots & images
│── README.md
```

---

## 📈 Key Learnings

✔ Azure Data Factory dynamic pipeline with ForEach
✔ Databricks transformation using PySpark
✔ External table creation with Synapse SQL
✔ Real-world OLTP → OLAP pipeline deployment process

---

## 🔮 Future Improvements

* Add CI/CD using Azure DevOps
* Scheduled automatic refresh using ADF triggers
* Power BI dashboard publishing

---

## ⭐ Support

If you like this project, please ⭐ star the repository!

---

## 👤 Author

**Harsh Vardhan Sahu**
B.Tech AI & ML | Data Engineer | ML Developer
