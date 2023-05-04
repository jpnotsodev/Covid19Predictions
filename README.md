
# COVID19 Forecasting using Azure Data Factory

The goal of this project is to create a data pipeline that can be used in real-world scenarios using Azure Data Factory (ADF). The data will be sourced from various locations, such as the European Centre for Disease
Prevention and Control (ECDC) and World Health Organization (WHO). 

This pipeline has four stages: ingest, process/transform, load and reporting.

### Prerequisites
- Azure Subscription

### Required Azure resources
- [Azure Data Factory](https://learn.microsoft.com/en-us/azure/data-factory/introduction) will be used for data orchestration of pipelines including ingestion, transformation and loading.
- [Azure Blob Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/) will be our secondary storage solution. This will act as a data store from which one of our data source will be copied and transferred into our primary storage solution.
- [Azure Data Lake Storage Gen2](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) will be our primary solution for storing both raw and processed data. 
- [Azure SQL Database]() stores and keeps processed data in the form of structured tables for querying, analysis and reporting.

### Solution Architecture
The diagram below outlines the data solution architecture use case for this project:

![image](https://github.com/jpnotsodev/Covid19Predictions/blob/master/img/339961933_189824550474508_8326684445169333129_n.png "Solution Architecture")

### How it works
1. A pipeline with a copy activity will be created to ingest data from ecdc website into our data lake storage.
2. The ingested raw data will then be transformed/curated using the following:
- `Mapping Data Flow` for transforming  **cases_and_deaths.csv** and **hospital_admissions.csv** data.
- `Databricks` - for transforming the **testing.csv** and **populations.csv** data.
3. Processed data will be stored inside a folder named **processed** available within our data lake storage.

### Stage 1: Ingestion

This section will describe how you can ingest data from multiple sources using [Copy Activity](). The Copy Activity is used to copy data from one location to another. An example scenario is when you want to copy data from a flat file source and then store it in a relational database such as SQL Database.

#### Download populations data and upload it into Azure Blob Storage

#### Ingest populations data into Azure Data Lake Gen2 using copy activity

1. Create a new pipeline
2. Under **Move & Transform**, select Copy Activity
3. Add a new or existing Source dataset to your Copy Activity
4. Add a new or existing Sink dataset to your Copy Activity
5. Click on **Publish All** to save changes

#### Add file validation (optional)

1. Under **General**, select **Validation activity**

#### Download covid related data from the ECDC website using HTTP connector

1. Browse to the Manage tab in your Azure Data Factory or Synapse workspace and select Linked Services, then click New.
2. Search for HTTP and select the HTTP connector.
3. Configure the service details, name it `HTTPLinkedService`, test the connection, and create the new linked service.
4. Create a dataset using your newly created linked service named `HTTPLinkedService`, text the connection, name it as `HTTPSourceDataSet`, then hit Create,
4. Create a new pipeline.
5. Under **Move & Transform**, select Copy activity.
6. Set Source dataset to `HTTPSourceDataSet`.
7. Set Sink dataset to `ADLSSinkDataSet`.

Your `raw` folder should look like the following:

```
\raw
    \populations
        populations.csv
    \cases and deaths
        cases_and_deaths.csv
    \hospital admissions
        hospital_admissions.csv
    \testing
        testing.csv
    ...
```

```
\processed
    \populations
        ._SUCCESS.crc
        .part-00000-896e21a0-5c3a-4545-951b-5e9aea971fbe-c000.csv.crc
        _SUCCESS
        part-00000-896e21a0-5c3a-4545-951b-5e9aea971fbe-c000.csv
        part-00001-896e21a0-5c3a-4545-951b-5e9aea971fbe-c000.csv
        part-00003-896e21a0-5c3a-4545-951b-5e9aea971fbe-c000.csv
        ...
```

### Stage 2: Transformation

### Stage 3: Store

### Stage 4: Reporting and Analysis

#### 
