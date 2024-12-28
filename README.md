# Spotify Data Pipeline with AWS Glue and QuickSight

![AWS Pipeline](https://github.com/user-attachments/assets/02785b72-e493-40cf-926c-8ffd786b3e5c)


This project demonstrates an end-to-end ETL pipeline using AWS services to process and analyze Spotify dataset. The architecture involves staging data in Amazon S3, transforming it using AWS Glue, and visualizing the insights with Amazon QuickSight.

---

## Architecture Overview

![Architecture](https://github.com/user-attachments/assets/4b530552-f738-45f6-b893-f11173fa8ef1)


### 1. **Data Ingestion and Staging**
- **Amazon S3 (Staging):**
  - Raw Spotify data is uploaded to an Amazon S3 bucket as the staging area.
  - Datasets include information about tracks, albums, and artists.

### 2. **Data Transformation and Processing**
- **AWS Glue ETL Job:**
  - AWS Glue is used to create an ETL pipeline that:
    - Reads data from the S3 staging bucket.
    - Performs data transformations, such as joins and field selections, using Glue Visual ETL.
    - Writes the transformed data to an S3 warehouse bucket.
  - **Pipeline Steps:**
    1. **Data Sources:**
        - Tracks, albums, and artist datasets are sourced from the S3 staging bucket.
    2. **Joins:**
        - `Join album and artist`: Combines album and artist data.
        - `Join`: Merges the joined album-artist data with track data.
    3. **Transformations:**
        - Unnecessary fields are dropped using a `DropFields` transformation.
    4. **Data Destination:**
        - The transformed dataset is stored in an S3 bucket (warehouse).

### 3. **Data Catalog and Querying**
- **AWS Glue Crawler:**
  - Crawls the transformed data stored in the S3 warehouse bucket.
  - Updates the AWS Glue Data Catalog with table schemas for querying.

- **Amazon Athena:**
  - Executes SQL queries on the Glue Data Catalog tables to analyze the data.

### 4. **Data Visualization**
- **Amazon QuickSight:**
  - Connects to Amazon Athena to visualize insights derived from the Spotify dataset.
  - Creates dashboards showcasing patterns in track popularity, artist trends, and more.

---

## Dataset
The dataset used in this project contains information about Spotify tracks, albums, and artists. It includes fields such as:
- **Tracks:** Track ID, name, duration, popularity, etc.
- **Albums:** Album ID, name, release date, etc.
- **Artists:** Artist ID, name, genre, etc.

---

## Prerequisites
To replicate this project, you need the following:
- An AWS account with permissions to use S3, Glue, Athena, and QuickSight.
- The Spotify dataset (or any dataset with similar structure).

---

## Steps to Recreate the Project

### 1. **Set Up S3 Buckets**
- Create two buckets in S3:
  - **Staging Bucket:** For raw data.
  - **Warehouse Bucket:** For transformed data.

### 2. **Upload Dataset**
- Upload the raw Spotify dataset to the staging bucket.

### 3. **Create AWS Glue ETL Job**
- Navigate to AWS Glue and set up an ETL job using Visual ETL.
- **Use the pipeline architecture shown below:**

 ![Pipeline ETL](https://github.com/user-attachments/assets/2a9f232a-bc63-4b11-8908-810cfe4640cc)


- Steps in the pipeline:
  1. Source data from S3 staging bucket.
  2. Join datasets (album, artist, and track).
  3. Perform field transformations.
  4. Output transformed data to the S3 warehouse bucket.

### 4. **Run Glue Crawler**
- Set up and run a crawler to update the Glue Data Catalog with the transformed data schema.

### 5. **Query Data with Athena**
- Use Amazon Athena to write SQL queries on the Data Catalog tables.
- Analyze trends, such as popular tracks and top artists.

### 6. **Visualize Data in QuickSight**
- Connect Amazon QuickSight to Athena.
- Create visual dashboards to showcase insights from the Spotify data.

---

## Key Features
- **End-to-End Automation:** From raw data ingestion to insights visualization.
- **Scalable Architecture:** Built using AWS services to handle large datasets.
- **User-Friendly Design:** Easy to replicate and modify for different datasets.

---

## Applications
- **Music Streaming Insights:** Understand trends in track popularity, artist growth, etc.
- **Data Engineering:** Learn how to design and deploy ETL pipelines using AWS Glue.
- **Data Visualization:** Build dashboards to derive actionable insights.

---

## Conclusion
This project demonstrates the power of AWS Glue, S3, Athena, and QuickSight in creating a robust data pipeline. The architecture can be easily adapted for other domains and datasets.

