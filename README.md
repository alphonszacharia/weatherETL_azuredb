# 🌦️ Weather Data Engineering Project – Azure Databricks

## 📌 Project Overview

This project demonstrates an end-to-end data engineering pipeline using **Azure Databricks, Apache Spark, Delta Lake and Open-Meteo API**.

The objective is to extract weather data from an external API, store raw data, transform it through Bronze, Silver and Gold layers, and build an interactive dashboard using Databricks AI/BI Dashboards.

The project follows the **Medallion Architecture** to organize data into three layers: Bronze, Silver and Gold.

## 🏗️ Architecture

```text
             Open-Meteo API
                    |
                    v
             Raw JSON Data
                    |
                    v
          Azure Databricks
                    |
                    v
             BRONZE LAYER
              (Raw Data)
                    |
                    v
             SILVER LAYER
          (Cleaned Data)
                    |
                    v
              GOLD LAYER
         (Aggregated Data)
                    |
                    v
            SQL Warehouse
                    |
                    v
         AI/BI Dashboard
                    |
                    v
          Weather Analytics
```

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Azure Databricks | Data engineering platform |
| Apache Spark | Distributed data processing |
| PySpark | Data transformation |
| Delta Lake | Reliable data storage |
| Open-Meteo API | Weather data source |
| SQL | Data querying and analysis |
| Databricks SQL Warehouse | Dashboard query execution |
| Databricks AI/BI Dashboards | Data visualization |

## 📂 Project Structure

```text
Weather-ETL-Project/
│
├── notebooks/
│   │
│   ├── 01_Extract_Weather_Data
│   │
│   ├── 02_Bronze_To_Silver
│   │
│   ├── 03_Silver_To_Gold
│   │
│   └── 04_Data_Validation
│
├── dashboard/
│   └── Weather_Analytics_Dashboard
│
└── README.md
```

## 🔄 ETL Pipeline Implementation

### 1. Data Extraction – Bronze Layer

- Connected to Open-Meteo Weather API using Python Requests.
- Extracted hourly weather information.
- Retrieved temperature, humidity, precipitation, wind speed and cloud cover.
- Stored the original API response as JSON in a Bronze Delta table.

**Table:** `bronze.weather_raw`

### 2. Data Transformation – Silver Layer

- Parsed raw JSON using PySpark.
- Applied an explicit Spark schema.
- Exploded hourly weather arrays into individual records.
- Renamed and cleaned columns.
- Removed duplicate records.
- Stored cleaned data in a Silver Delta table.

**Table:** `silver.weather_cleaned`

### 3. Data Aggregation – Gold Layer

Performed daily aggregations, including:

- Average temperature.
- Maximum temperature.
- Minimum temperature.
- Average humidity.
- Total rainfall.
- Average wind speed.
- Average cloud cover.

Stored the aggregated results in the Gold Delta table.

**Table:** `gold.weather_summary`

### 4. Data Visualization

Created an interactive Weather Analytics Dashboard using Databricks AI/BI Dashboards.

Dashboard metrics include:

- Average temperature.
- Maximum temperature.
- Minimum temperature.
- Daily rainfall.
- Average humidity.
- Wind speed trends.

## 📊 Dashboard

The dashboard provides an analytical view of weather conditions using the Gold layer.

It enables users to understand daily temperature changes, rainfall patterns, humidity levels and wind speed.

## 💾 Data Storage

The project uses Delta Lake for storing Bronze, Silver and Gold tables.

Delta Lake provides:

- ACID transactions.
- Schema enforcement.
- Time travel.
- UPDATE, DELETE and MERGE operations.
- Reliable data management.

Delta tables store their underlying data in Parquet files and maintain transaction information in the `_delta_log` directory.

## 📍 Data Source

**Open-Meteo API**

Weather data was extracted using the Open-Meteo Forecast API.

Location used: Thodupuzha, Kerala, India.

Coordinates:
- Latitude: 9.894
- Longitude: 76.718

## 🎯 Key Learning Outcomes

Through this project, I gained practical experience in:

1. Working with REST APIs.
2. Extracting data using Python.
3. Building ETL pipelines using Azure Databricks.
4. Implementing Medallion Architecture.
5. Processing JSON using PySpark.
6. Working with Delta Lake tables.
7. Performing aggregations using Spark SQL.
8. Understanding Databricks SQL Warehouse.
9. Creating interactive AI/BI dashboards.
10. Understanding data engineering workflows.

## 🚀 Future Enhancements

- Implement incremental data loading.
- Use Delta MERGE for upsert operations.
- Add data quality validation.
- Implement error handling and logging.
- Orchestrate notebooks using Databricks Workflows.
- Add automated pipeline monitoring.
- Integrate Power BI for external reporting.

## 👨‍💻 Author

Azure Databricks Data Engineering Project

**Project:** Weather Data ETL Pipeline

**Platform:** Microsoft Azure Databricks
