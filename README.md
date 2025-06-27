# Cloud Data Fusion ETL Pipeline with JDBC Sink

This project demonstrates how to extract data from a Cloud Storage CSV file and load it into a MySQL database using Google Cloud Data Fusion.

---

## Features

- Uses **Cloud Data Fusion** for graphical ETL pipelines
- Reads data from Google Cloud Storage
- Loads data into a MySQL database using JDBC
- Supports parameterized (dynamic) pipeline variables
- Designed for incremental loads

---

##  Requirements

- Google Cloud Project
- Cloud Data Fusion instance
- Google Cloud Storage bucket (with your CSV files)
- MySQL database (e.g., Cloud SQL)
- MySQL JDBC driver (installed via Data Fusion Hub)

---

##  Pipeline Overview

1. **Source**: GCS (Google Cloud Storage)  
   - File format: CSV
   - Path: `gs://<your-bucket>/<your-file>.csv`

2. **Sink**: MySQL Database (using JDBC plugin)  
   - JDBC Plugin: `mysql`  
   - JDBC Driver Class: `com.mysql.cj.jdbc.Driver`  
   - Connection string: `jdbc:mysql://<host>:3306/<dbname>`  
   - Username & Password: as configured

3. **Transformations**:  
   - Data parsing (e.g., CSV parsing)
   - Schema mapping
   - Optional: filter / deduplication logic

4. **Deployment**:  
   - Designed in Data Fusion Studio  
   - Can be scheduled to run daily
   - Supports parameterized runtime arguments for flexibility

---

##  How to Run

1. Create a Cloud Data Fusion instance
2. Upload the JDBC driver (MySQL) from the **Hub**
3. Design the pipeline:
   - Add a GCS source
   - Add a Database sink
   - Connect them in the canvas
4. Configure:
   - JDBC Plugin Name: `mysql`
   - JDBC Driver Class: `com.mysql.cj.jdbc.Driver`
   - Connection String: `jdbc:mysql://<your-host>:3306/<your-db>`
5. Deploy the pipeline
6. Trigger manually or schedule via triggers

---

## Parameters Example

You can parameterize the connection string:

```bash
host=35.123.123.5
port=3306
dbname=mydb
user=root
password=secret
