# AdventureWorks-Azure-End-To-End-Data-Engineering-Project

Skill Used In this project-  Azure Data Factory, Azure Databricks,Azure Data Lake Storage Gen2, Pyspark, Azure Synapse Analytics and Power-BI Tool

1-How to design and implement a robust data pipeline using Azure Data Factory.

2-The process of data integration and transformation with Databricks.

3-Utilizing Azure Synapse Analytics for efficient data warehousing and analytics.

4-Best practices for handling big data solutions and real-time data processing with Apache Spark.

5-Connecting Power-BI with our Azure Synapse Analytics workspace. This integration is required to access the curated datasets and begin developing the required reports and dashboards.

![Uploading image.png…]()


# Implementation Steps To Create Dynamic Pipeline:

Create Linked Services
Configure the source and destination linked services to establish connectivity with GitHub (via HTTP) and Azure Data Lake Storage, respectively.
Configure Copy Activity
Use a Copy Activity to move data from the source to the destination.
Source Dataset:
Configure the dataset using an HTTP connection.
Create a parameter p_relativeURL to handle varying relative URLs, as the base URL remains constant.
Sink Dataset:
Configure the dataset using an Azure Data Lake connection.
Create parameters p_folder and p_filename to dynamically define the target folder path and file name.
Use Lookup and ForEach Activities
Create a Lookup Activity with a dataset containing a JSON array that holds metadata such as p_relativeURL, p_filename, and p_folder.

Configure a ForEach Activity to iterate over the lookup output using:
@activity('Lookup').output.value

Enable sequential execution if required.
Within the ForEach loop, use a Copy Activity to fetch and load each file individually into the Data Lake Storage Gen2.
