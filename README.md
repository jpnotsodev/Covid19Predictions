
# Project on COVID19 Cases

The goal of this project is to create a data pipeline that can be used in real-world scenarios using Azure Data Factory (ADF). The data will be sourced from various locations, such as the European Centre for Disease
Prevention and Control (ECDC) and World Health Organization (WHO). 

The data will then be ingested into Azure Data Lake Gen2, using ADF. Once the data is stored in the data lake, various data transformation techniques will be used to analyze and transform the data.

## Components
- Azure Data Factory
- Azure Key Vault
- Azure Blob Storage
- Azure Data Lake Storage Gen2


## Data Ingestion
To ingest data into our Azure Data Lake Storage, we'll be using a [copy activity](#http://google.com). Copy Activity let's you copy data from one data store to another, and is capable of bringing data that are both on-premise and in cloud.

To use a Copy Activity, you'll have to do the following:

- Create a Linked Service (for both sink and source)
- Create a Dataset
- Create a Pipeline with a Copy Activity

## Data Transformation
