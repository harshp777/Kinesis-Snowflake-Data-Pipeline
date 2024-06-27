# Kinesis-Snowflake-Data-Pipeline

This project exemplifies a robust and scalable approach to building a modern data pipeline, integrating streaming data ingestion with advanced data processing and transformation, making it an impressive addition to any data engineering portfolio.

![image](https://github.com/harshp777/Kinesis-Snowflake-Data-Pipeline/assets/58933098/67b966e2-f2e3-4623-8a42-38dc811d0560)


# Kinesis-Snowflake Data Pipeline Project

The **Kinesis-Snowflake Data Pipeline Project** is an end-to-end data pipeline leveraging various AWS services and Snowflake to efficiently handle and process streaming data. This project showcases the seamless integration of cloud-based data ingestion, processing, and transformation workflows.

## Architecture Overview

The architecture of this data pipeline involves several key components, as illustrated in the diagram below:

![Architecture Diagram](assets/img/portfolio_pic2.jfif)

1. **Data Source (EC2 Instance)**:
   - The data pipeline starts with an EC2 instance, which serves as an application emitting logs. This instance holds customer and order datasets, simulating real-time data generation.

2. **Kinesis Agent**:
   - A Kinesis Agent installed on the EC2 instance captures the streaming data logs and sends them to Kinesis Data Firehose.

3. **Kinesis Data Firehose**:
   - Kinesis Data Firehose acts as the data transport layer, continuously delivering the streaming data to Amazon S3.

4. **Amazon S3 Zones**:
   - The data pipeline employs three distinct S3 zones:
     - **Landing Zone**: Initial storage location for raw data ingested from Kinesis Firehose.
     - **Processing Zone**: Intermediate storage where data transformation and processing take place.
     - **Processed Zone**: Final storage location for the transformed and processed data.

5. **Apache Airflow (MWAA)**:
   - Apache Airflow, managed via Amazon Managed Workflows for Apache Airflow (MWAA), orchestrates the data pipeline. The Airflow Directed Acyclic Graphs (DAGs) manage the data transfer and processing workflows.
   - The DAGs are triggered to move data from the Landing Zone to the Processing Zone.

6. **Snowflake**:
   - Snowflake performs data ingestion and transformation operations in the Processing Zone. It processes the data, ensuring it is clean and structured.
   - Once the transformation is complete, the processed data is stored back in the S3 Processed Zone for further analysis or downstream processing.

## Workflow

1. **Data Ingestion**:
   - The EC2 instance generates logs containing customer and order data.
   - The Kinesis Agent captures these logs and streams them to Kinesis Data Firehose.

2. **Data Delivery to S3**:
   - Kinesis Data Firehose delivers the raw data to the S3 Landing Zone.

3. **Data Processing**:
   - Apache Airflow DAGs trigger data transfer from the Landing Zone to the Processing Zone.
   - Within the Processing Zone, Snowflake ingests the data and performs necessary transformations.

4. **Storing Processed Data**:
   - The transformed data is moved to the S3 Processed Zone for storage.

## Key Benefits

- **Scalability**: The architecture leverages AWS services that can scale with increasing data volumes.
- **Real-Time Processing**: Kinesis Data Firehose ensures real-time data streaming and ingestion.
- **Efficient Orchestration**: Apache Airflow automates and manages complex data workflows.
- **Robust Data Transformation**: Snowflake provides powerful data transformation capabilities.
- **Cost-Effective Storage**: Amazon S3 offers cost-effective and durable storage for raw and processed data.




