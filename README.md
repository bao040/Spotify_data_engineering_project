# Spotify Data Engineering Project

---
The workflow diagram:

![Data Flow Diagram](https://github.com/bao040/Spotify_data_engineering_project/blob/main/worflow_diagram.png)


## **Project** **Overview**

This data engineering project focuses on processing and managing data from the Spotify API. The goal is to extract, transform, and load (ETL) the data efficiently using Python, AWS services, and Snowflake. The processed data is stored in Amazon S3 and later loaded into Snowflake as a data warehouse.

---

## **Data Flow**

The workflow involves several key steps as depicted in the diagram:

1. **Fetch Spotify Data:**
   - This step involves connecting to the Spotify API to fetch raw data related to songs, artists, and albums.

2. **Upload Raw Data to S3:**
   - The fetched data is uploaded into S3 Bucket as raw JSON format.

3. **Read Data from S3:**
   - The raw data stored in S3 is retrieved for processing. This step ensures the data is ready for transformation.

4. **Process and Store Data Temporarily:**
   - Raw data will be processed and extracted necessary information for 3 objects: songs, artists and albums. This stage includes data extraction skills with Python in Apache Airflow platform.
   - Processed data then is stored temporarily in S3 Bucket with 3 seperated folders, each for albums, artists and songs.
     
The data is processed paralelly in Apache Airflow:

![Data Flow Diagram](https://github.com/bao040/Spotify_data_engineering_project/blob/main/paralel.png)

5. **Load Data into Snowflake:**

   - **Tools:** `Snowpipe`, `Snowflake`
   - The processed data stored in S3 is loaded into Snowflake using Snowpipe. This step ensures the data is ingested into the Snowflake data warehouse in a structured and queryable format.

---

## **Workflow Execution**

- The workflow is orchestrated using Python, with tasks defined and executed sequentially or in parallel as necessary.
- The `PythonOperator` handles custom Python scripts for data extraction and transformation.
- The `S3CreateObjectOperator` is used for saving data to S3, ensuring that the raw and processed data is efficiently managed and accessible.
- `Snowpipe` automates the loading of processed data from S3 into Snowflake.

---

## **AWS and Snowflake Integration**

- **Amazon S3:** Acts as the central storage for both raw and processed data.
- **Python:** Used to fetch, process, and manipulate the data throughout the pipeline.
- **Snowpipe and Snowflake:** Enables real-time data ingestion and provides a powerful data warehouse for analytics.

---

This project structure ensures a scalable and modular approach to data engineering, providing a clear path for enhancements and integrations in the future.

