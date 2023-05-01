
# Project on COVID19 Cases

The goal of this project is to create a data pipeline that can be used in real-world scenarios using Azure Data Factory (ADF). The data will be sourced from various locations, such as the European Centre for Disease
Prevention and Control (ECDC) and World Health Organization (WHO). 

The data will then be ingested into Azure Data Lake Gen2, using ADF. Once the data is stored in the data lake, various data transformation techniques will be used to analyze and transform the data.

## Components
- Azure Data Factory
- Azure Key Vault
- Azure Blob Storage
- Azure Data Lake Storage Gen2

## Solution Architecture
![image](https://github.com/jpnotsodev/Covid19Predictions/blob/master/img/339961933_189824550474508_8326684445169333129_n.png "Solution Architecture")


## Dataflow
### Ingestion
- A pipeline with a copy activity will be created to ingest data from one data store to another.
- The ingested data will be stored in our data lake storage gen2, 
