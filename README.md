# data-analyst-sidat

<h1 align="center">Project Description: Descriptive Analysis of Common Property Types</h1>

<h1 align="center">Project Part 1: Property Tax Data Analytical Platform</h1>

**Dataset:** Property Tax Report

Property Tax Report URL: https://opendata.vancouver.ca/explore/dataset/property-tax-report/information/?sort=-tax_assessment_year&dataChart


## **Objectives:**

The Property Tax Data Analytical Platform project is designed to help analyze the property tax records for the City of Vancouver. The project is structured using AWS Services to perform data ingestion, storage, preparation, cleaning, transformation, and visualization tasks. It addresses four key analytical questions through descriptive, diagnostic, predictive, and prescriptive analysis.

![image](https://github.com/user-attachments/assets/bf292cf9-d12b-4d0c-8d3f-98544a25c6b1)

## **Data Analytical Question Formulation**

To evaluate the property tax dataset, four types of analytical questions were formulated:

**Descriptive:** "What are the common property types (residential/commercial) in the dataset?"

**Diagnostic:** "What different factors contribute to property tax variation?"

**Predictive:** "What will be the percentage increase/decrease in property tax next year?"

**Prescriptive:** "What incentives can encourage timely tax payments? What penalties should be imposed for late payments?"


## **Data Discovery**

**Key dataset variables include:**

**PID:** Property Identifier - A unique number assigned to each property.

**Legal Type:** The legal classification of the property (e.g., LAND, STRATA).

**Folio:** A unique identifier for the property, often used in tax records.

**Land Coordinates:** A coordinate or identifier related to the property’s location on a land grid.

**Zoning District:** The zoning code assigned to the property, indicating the permitted uses.

**Zoning Classification:** A broader classification of zoning, such as Residential, Commercial, etc.

**Lot:** The lot number within a subdivision or block.

**Plan:** The plan number associated with the subdivision or land development plan.

**Block:** The block number within a plan or subdivision.

**District Lot:** The district or area in which the property is located.

**Street Name:** The name of the street where the property is located.

**Current Land Value:** The assessed value of the land portion of the property for the current year.

**Current Improvement Value:** The assessed value of any improvements on the property for the following tax year.

**Tax Assessment year:** The year for which the property tax assessment applies.

**Year Built:** The year the primary structure on the property was built.

**Report Year:** The year in which this data was reported

![image](https://github.com/user-attachments/assets/1a4d5faa-e205-4695-863f-1933dc4f74ff)

## **Methodology** 

**1: Data Storage Design**

**S3 bucket structure:**

**S3 Path:** s3://property-tax-activity-sidat/property-tax/review-reports/

**Subfolders:**2023, 2024, containing datasets like Property Tax Records, Municipal Financial Reports, Property Value Database, and Tax Payment Records.

![image](https://github.com/user-attachments/assets/eccbe42b-a635-4972-b4ee-03be2ab08f8d)

**2: Dataset Preparation**

**Tool:** AWS DataBrew

**Key tasks:**

Removal of rows with empty values.

Dropping less relevant columns (e.g., Land Coordinates, District Lot).

Conversion of numerical data types to integers.

Two DataBrew jobs were created: Proptax-Job-2023 and Proptax-Job-2024.


**3: Data Ingestion, Storage, Pipeline Design, Cleaning, Pipeline Implementation.**

AWS Glue ETL Job: Proptax-ETL-job

Imported datasets for 2023 and 2024 from S3 raw folder.

Changed schema, filtered out irrelevant rows, and dropped null values.

Used join and aggregate functions to combine datasets and focus on zoning classification.

AWS Glue's ETL process cleaned and transformed the data:

Targeted crucial dataset variables such as Zoning Classification.

Combined data for multiple years and removed irrelevant or incomplete data.

Final filtered data stored in the curated S3 folder in CSV format.

The ETL Pipeline was implemented using AWS Glue, storing the cleaned datasets in the curated folder of the S3 bucket.

![image](https://github.com/user-attachments/assets/b812e6b3-54e6-4546-bacc-4ebc2b5c3a66)

**4: Data Structuring**

**Tool:** AWS Athena

Created a SQL-based table to store curated data and enable queries for further analysis.

![image](https://github.com/user-attachments/assets/b67d4ae4-31f1-4763-923e-8305ce08d3fb)


**5: Data Analysis and Visualization**

Extracted refined data from AWS Athena in CSV format.

Visualization: Used Excel to create a pie chart, representing different property zoning types.

![Web server screenshot cloud assignment](https://github.com/user-attachments/assets/4b55ce49-d8ed-4754-8fb3-8c77126b7959)

 

**6: Data Protection**

**Tool:** AWS KMS (Key Management Services)

Provided protection to the Dataset 'Property Tax Records" to provide access only to authorized users.

To avoid accidental data deletion and multiple region accessbility, S3 Versioning and Cross-Region Replication is enabled.


**7: Data Monitoring**

**Tools:** AWS CloudWatch and AWS CloudTrail

Real-Time Monitoring, Enhanced Security Monitoring, Historical Data Analysis conducted.

![image](https://github.com/user-attachments/assets/52a85f62-0c17-45df-b87d-44731b8f2b27)

## **Data Insights and Findings**

**Zoning Classifications:** Properties evaluated in both years were mostly being used as commercial properties.

## **Recommendation**

To enhance the analysis and management of the Property Tax Records dataset, it is recommended to implement regular updates and reviews of the encryption and protection measures to address evolving security threats. Continuously monitor and adjust the data governance processes using AWS Glue DataBrew to refine data quality and adapt to any changes in data structure or quality issues. Incorporate more advanced visualizations and statistical analyses to uncover deeper insights and trends in property tax data. Additionally, set up automated alerts in AWS CloudWatch to proactively identify and respond to any anomalies or performance issues, ensuring that the dataset remains reliable and actionable for informed decision-making.


## **Tools and Techniques**

 1- AWS S3 Bucket
 
 2- AWS Glue
 
 3- AWS Glue DataBrew
 
 4- AWS Athena
 
 5- AWS EC2
 
 6- AWS KMS (Key Management Services)
 
 7- AWS CloudWatch
 
 8- AWS CloudTrail

## **Deliverables**

1- **Data Questions and Discovery**

2- **S3 Storage Structure**

3- **Cleaned Datasets** for 2023 and 2024

4- **ETL Pipeline** Design and Implementation (AWS Glue)

5- **Structured SQL Queries** in AWS Athena

6- **Visualizations** (Charts in MS Excel)

7- **Data Published** on General and Web Servers (EC2 Instances)

8- **Data Protection** (AWS KMS encryption)

9- **S3 Versioning** for data history

10- **Cross-Region Replication** for data availability

These deliverables provide a comprehensive framework for analyzing property tax data, ensuring data is securely stored, processed, and published while maintaining integrity and availability.

## **Conclusion**


This data analytics initiative helps the City of Vancouver make informed decisions that support local businesses and residents. By analyzing trends in zoning classifications for properties, the city can refine urban planning, boost the local economy, improve public services, and promote sustainable development.
