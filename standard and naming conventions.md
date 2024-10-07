# Vensure project conventions - draft 

## 1. Architecture attributes

**- scale out**: Vensure and its clients use various data sources like Prism API, Snowflake data views, ClientSpace API, Smartsheet, Excel, and invoices in PDF, Word, and Excel. They produce spreadsheets for daily operations, analysis, and monitoring. With multiple clients and ongoing acquisitions, the number of data sources and mapping requirements is constantly growing, necessitating an evolving design.

**- reuse** : Even with numerous sources, clients, and outputs, the structure and pipelines are similar and can be combined from source to destination, such as:

feeding : 

a) from smartsheet to lakehouse
b) from multiple format files to lakehouse
c) from snowflake to lakehouse
d) from api to lakehouse

producing: 

e) from lakehouse to smartsheet
f) from lakehouse to spreadsheet
f) from lakehouse to powerbi/fabric/AI/dev

With the lakehouse as the main repository, information can be delivered in multiple formats, destinations, to authorized users, views, apps, and smart agents. 

To achieve this, it's essential to template the data ingestion process and customize transformation rules based on specific projects and business tasks. This approach ensures a universal, clean, and optimized data consolidation.

**- Single Source of Truth**: Ensure that the universal data consolidation avoids any repeated information. While data can be duplicated during staging, it must be centralized in production. Additionally, remove any data garbage in staging to control storage costs.

**- Timely**: Customize the data feeding schedules based on the requirements of each project to ensure timely data availability.

**- Standardized**: Establish consistent naming conventions and architectural standards to prevent uncontrolled growth and facilitate easy maintenance of Fabric and cloud infrastructure components by any consultant in the future.


## 2. Folders and Workspace Structure 

Organize your work into logical **workspaces** and **folders** to ensure scalability and ease of navigation as your solution grows.

- **Workspaces**: 

Create separate workspaces for different functional areas or departments, using the following naming convention: the first letter of each word should be uppercase, and subsequent words should be separated by underscores and in lowercase. For example: 

- `Ingestion` (for raw data extraction from APIs and files)
- `Transformation` (for data cleaning, transformation)
- `Validation` (for data validation ensuring data correctness)
- `Output` (for storing final datasets)

or include the department or project: 

- `Ingestion_codesmaping` (for raw data extraction from APIs and files)
- `Transformation_salesdashboard` (for data cleaning, transformation)
- `Output_salesdashboard` (for storing final datasets)

  
- **Folders**: 
Within each workspace, create folders for specific data sources (APIs and spreadsheets) and operations. Use the following naming convention: the first letter should be lowercase, and the first letter of subsequent words should be uppercase. For example: 

- **Ingestion/apis** (for pipelines related to APIs)
- **Ingestion/spreadsheets** (for pipelines related to spreadsheet data)
- **Transformation/benefitsTransforms** (for shared transformation logic)
- **Output/processed** (for output data)

## 3. Naming Conventions

Naming should be descriptive yet concise, with consistent patterns for easy identification. Below are suggestions for naming various components, a general sintax include:  


### components convention

__<component type>_<source type>_to_<destiny type>_<descriptive name>_<version>__

__component type__: pipe, rule, template, conn, powerquery, activator, dataflow, trigger, etc. 

__source type__ : api, prism, clientspace, excel

__destiny type__ : lakehouse, warehouse, excel, smartsheet, api 

__descriptive name__ : removenullvalues, generateBenefitTransforms, validateData, copyInvoicesToOneDrive


Some examples: 
- `pipe_prism__lakehouse_loadClients_v1`
- `pipe_excel__lakehouse_loadSalesLeads_v2`
- `dataflow_lakehouse_spreadsheet_salesForecast_v2`
- `dataflow_lakehouse_lakehouse_cleanEmptyEmployees_v1`

### parameters, variables, connections
all parameters names must start with "p" and all the variables with "v", such as `pUrl, pMoneyLimit, vRentTax, vTotal`. As well, all connection names start with conn prefix and the name of the destiny connection such as: `connPrism, connClientSpace, connSnowflake`. 


## 4. Reusable Components

To ensure maximum reuse, break down common functionalities into reusable components:

- **Parameterization**: 

Use parameters for API URLs, authentication keys, file paths, and date ranges. This allows you to configure the same pipeline for different APIs and spreadsheets without duplicating code.
  
- **Templates for Pipelines**:

Create a **pipeline template** for API extraction and another for spreadsheet ingestion and so on, common behaviors must be build by templates configured by parameters 

- **Shared Transformations**:

For common transformations (e.g., data cleaning, validation), create separate **dataflows** or activities that can be reused in multiple pipelines.
  
- **Connection Reuse**:

Set up shared connections for API calls, file storage (OneDrive, SharePoint), and databases. These can be reused across multiple pipelines.

## 5. Modular Design Strategy

As the number of APIs and spreadsheets grows, a **modular design strategy** will help in scaling and maintaining pipelines:

- Separate the data extraction process from each data source (API, spreadsheet). Each pipeline that handles data extraction should focus solely on one API or file type.
  
- Create independent pipelines for **data transformations** that can be reused. This allows you to apply standard transformations across different datasets without duplicating logic.

- Use a **master pipeline** to orchestrate the execution of individual data pipelines. The master pipeline will trigger the appropriate extraction and transformation pipelines based on schedules or conditions.


## 6. Error Handling and Logging

Standardize error handling and logging to simplify troubleshooting and monitoring: 

- Implement centralized logging for errors and performance tracking. For each pipeline, include an activity that logs errors to a standard location (e.g., SQL table, Data Lake).
    
- Implement retry mechanisms in the pipelines for transient API failures (e.g., rate limiting, network issues). Add retries to critical API calls to improve robustness.

- Add comments and document each pipeline’s purpose and key changes. This helps team members understand the context and intent of each pipeline.

- Use the **Monitor** section in Fabric to track pipeline execution status and performance.

- Set up alerts for failures or delays in execution.

- Automate notifications (e.g., via email) when an API call fails or a spreadsheet file cannot be processed.

## 7. data governance 
pending to define for this first version

Data governance is the practice of managing and organizing data to ensure its quality, security, and availability. It involves defining policies, standards, and procedures for data collection, storage, processing, and usage. The main goals of data governance are to maintain data integrity, ensure compliance with regulations, and enable data-driven decision-making.

Effective data governance helps organizations create a single source of truth, reduce data silos, and improve data quality. It also enhances collaboration, ensures data privacy, and supports regulatory compliance. 