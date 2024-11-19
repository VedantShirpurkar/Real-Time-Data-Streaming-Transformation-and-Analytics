# Real-Time-Data-Streaming-Transformation-and-Analytics
This project demonstrates the implementation of a real-time data streaming pipeline leveraging tools like Apache NiFi, Amazon S3, Snowflake Snowpipe, Streams, and Tasks. The pipeline processes and loads data efficiently, handling large volumes (10,000 rows in one go), and ensures timely ingestion and transformation into the target system for analytical use cases.

Workflow Overview
Data Source and Apache NiFi on Amazon EC2:

The pipeline begins with Apache NiFi, an open-source data integration and streaming platform deployed on an Amazon EC2 instance.
NiFi is used to extract, process, and send data to the next stage in the pipeline. It ensures seamless handling of real-time data streams and facilitates dynamic routing and transformation.
Amazon S3 as a Data Lake:

Processed data from NiFi is written to Amazon S3, which acts as a temporary storage layer (data lake).
S3 provides durability and scalability to store the intermediate data before ingestion into Snowflake.
Snowflake Snowpipe for Continuous Data Ingestion:

Data files from Amazon S3 are ingested into Snowflake using Snowpipe, an automated and scalable service that loads data into staging tables in near real-time.
Snowpipe listens to S3 bucket events and triggers ingestion as soon as new files are added.
Staging Table in Snowflake:

A Snowflake Task automates the processing of the captured data. Tasks execute SQL-based transformations to cleanse, enrich, and load data from the staging table into final target tables.
The transformed data is distributed into Target Table 1 and Target Table 2, representing different downstream requirements.
Target Tables:

The final processed data is stored in target tables, which are optimized for analytical workloads.
These tables enable efficient querying and reporting for real-time insights.
Key Features
Real-Time Data Processing: Ensures timely ingestion and transformation of data with minimal latency.
Scalable Architecture: Uses scalable cloud-native services like Amazon S3, Snowflake, and NiFi for handling large data volumes (10,000 rows in one go).
Automated Data Loading: Snowpipe automates the ingestion process, reducing manual intervention.
Change Data Capture (CDC): Snowflake Streams track incremental changes, allowing efficient processing.
End-to-End Automation: Snowflake Tasks automate SQL transformations, ensuring a seamless data pipeline.
Technologies Used
Apache NiFi: For real-time data ingestion and processing.
Amazon EC2: To host Apache NiFi.
Amazon S3: For scalable and durable data storage.
Snowflake: For cloud data warehousing, including Snowpipe, Streams, and Tasks.
How It Works
Deploy Apache NiFi on an EC2 instance to capture and preprocess data from a source system.
Configure NiFi to send processed data to an Amazon S3 bucket.
Set up Snowpipe to monitor the S3 bucket for new files and ingest them into Snowflake's staging table.
Create a Snowflake Stream to track changes in the staging table.
Define a Snowflake Task to process and transform the captured changes and load the results into the final target tables.
Use Case
This pipeline is ideal for scenarios requiring real-time data processing and transformation, such as:

Streaming analytics for business intelligence.
ETL workflows for near real-time data integration.
Building dashboards that require up-to-date data.
Project Highlights
Batch Size: Handles 10,000 rows per batch for efficient bulk loading.
Real-Time Insights: Enables near real-time analytics by continuously updating target tables.
Cloud-Native: Fully leverages cloud infrastructure for scalability, reliability, and cost efficiency.
