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

![Architecture Diagram](https://drive.google.com/uc?export=view&id=1fbZLVHHXvhsZ5KfwJbaIX24nHThcptz1)

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

![ADF Pipeline](https://drive.google.com/uc?export=view&id=1W5pIRjon_g89KbsRk2CGm1Yk14FVM9rZ)

### Preview of input JSON file in Lookup

![Lookup](https://drive.google.com/uc?export=view&id=1J-qc0KpcMK6WS6Huo_FaU1FhCiwW66JH)

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

![Cleaning Code](https://drive.google.com/uc?export=view&id=10sBoYNXHpYLQ2WIxykPAMOhV-XKH9ieY)

### Timestamp Conversion Example

![Timestamp](https://drive.google.com/file/d/1yZ-BU77PrCAMtxPVZ2CPF0bxfi7NEtG3/view?usp=drive_link)

---

## 📊 Data Visualization in Databricks

Example visualization of delivery delay grouped by payment type:

![Visualization](https://drive.google.com/file/d/1bpHvsyrWSq7Evl4n6oeAFajQsIpDSKZO/view?usp=drive_link)

---

## 🟢 Enrichment Layer using MongoDB

Reading reference table using PyMongo and joining with transformed layer.

![Mongo](https://drive.google.com/file/d/14kG_ShF1pWyI0YQGquoW22CRIYjbOQEb/view?usp=drive_link)

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

![Synapse Query](https://drive.google.com/uc?export=view&id=1ppnahrHBrR74jqGx1Vh9nstSbBaSXdcm)
![Synapse Query](https://drive.google.com/uc?export=view&id=1ppnahrHBrR74jqGx1Vh9nstSbBaSXdcm)

---

## 📊 Dashboard / Visualization

Business-ready output available for BI tools.


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
