# Azure Fabric

## General vision of Fabric
One Lake, Everything goes to onelake, eliminating silos. 
One Copy, just one dataset, with shortcuts
One format, delta parquet 
One user experience
One access control method
One security model
One governance model
One monitoring hub
One licensing structure

## The 7 experiences 

Fabric comes with 7 experiences

1. Data factory 

- make ETLS
- dataflow, connect sources and destiny with transformation
- pipeline to schedule ETL operations

2. Synapse data warehouse 

- data warehouse, similar to SQL server
- tables, schemas, views, stored procedures, TSQL

3. Synapse data engineering 

- design, build and maintain infraestructure and systems to collect, store, process and analyze large data
- lake house
- structured and unstructured data
- representations as 
- it use notebooks in R , Scala or Pythong
- also it has spark jobs

4. Synapse data science 

- data exploration, preparation of cleansing to experiment, modeling, model scoring, service predictive insights to powerbi
- notebook
- experiments

5. Synapse real time analytics

6. Power BI

7. Data Activator

## the 3 data stores

It has 3 data stores, los 3 automáticamente salva todo en onelake con el unico formato delta parquet

Data Warehouse: Choose this when you need structured data storage optimized for complex queries and reporting. 

Lakehouse: Opt for this when you need a flexible storage solution that supports a variety of data types and both batch and real-time processing. 

KQL Database: Use this for scenarios requiring fast querying of log and telemetry data, such as real-time monitoring and operational analytics123. 


### 1. data warehouse

Schema-on-Write: Data must be structured and cleaned before loading.
SQL MPP Engine: Supports full T-SQL DDL and DML operations.
Optimized for Analytics: Designed for complex queries and reporting. 

Use Cases: 

Business Intelligence: Ideal for structured data and running complex queries for reporting and analytics.
Historical Data Analysis: Suitable for analyzing historical data trends and patterns. 

### 2. lakehouse 

Unified Storage: Combines the features of data lakes and data warehouses.
Supports All Data Types: Can store structured, semi-structured, and unstructured data.
Delta Tables: Provides ACID transactions and scalable metadata handling. 

Use Cases: 

Data Science and Machine Learning: Great for storing and processing large volumes of diverse data types.
Real-Time Analytics: Suitable for scenarios requiring both batch and streaming data processing.

### 3. KQL database

Optimized for Log and Time-Series Data: Designed for fast querying of large volumes of log and telemetry data.
Schema-on-Read: Data can be ingested without predefined schema and queried on demand.
KQL Syntax: Uses a specialized query language optimized for log and telemetry data.

Use Cases: 

Real-Time Monitoring: Ideal for monitoring applications, infrastructure, and security logs.
Operational Analytics: Suitable for analyzing time-series data and operational metrics.

## 4 computes engines

1. TSQL
2. Spark engine (python, R, Scala)
3. KQL engine
4. Analysis service

## procesos en Fabric


## 1. data ingestion

**fabric data factory**

**real time analytics**

## 2. data storage

**lake house**

**data warehouse**

**kql database**

## 3. aata engineering & science

**data engineering**

**data science**

## 4. business intelligence

**power bi**



