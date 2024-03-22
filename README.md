# Google-Big-Query-Guide

## Introduction to Bigquery

BigQuery is a fully managed, serverless data warehouse solution provided by Google Cloud Platform (GCP). It allows users to analyze massive datasets using SQL queries quickly and efficiently, without the need for managing infrastructure or provisioning resources. It also extends support to Machine Learning, Data Analysis and Buisness Intelligence.

| Feature            | BigQuery                             | Traditional Databases               |
|--------------------|--------------------------------------|------------------------------------|
| **Scalability**    | Scales seamlessly to petabytes of data | Limited scalability, often constrained by hardware limitations |
| **Performance**    | High-speed query processing           | Performance may degrade with large datasets or complex queries |
| **Serverless**     | Fully managed, no infrastructure setup required | Requires managing servers, databases, and infrastructure |
| **Cost-Effective** | Pay-as-you-go pricing model based on data processed | Upfront hardware and licensing costs, ongoing maintenance |
| **Integration**    | Native integration with other GCP services | May require additional configuration for integration with other services |
| **Concurrency**    | Supports high concurrency queries     | Limited concurrency depending on database configuration |
| **Security**       | Built-in security features, including IAM and encryption | Security measures need to be implemented and managed |


## Getting Started 

Please perform the following steps :- 

1. Navigate to the following link [BigQuery-Start-page](https://cloud.google.com/bigquery?hl=en) . Click on the following button "Try BigQuery Free"
2. You will be navigated to the following Sign up page [Sign Up](https://console.cloud.google.com/freetrial/signup/tos)
3. On the Billing page [Billing_Page](https://console.cloud.google.com/freetrial/signup/billing/NL). Enter the details and click on "Start Free"

Please note that you will be provide with free 300$ credits and then you will be charged accordingly. No automatic charges are deducted. 


## Understanding the UI

### Accessing the Console:

1. Go to the Google Cloud Console: [Console Page](https://console.cloud.google.com).
2. Click the Navigation menu (three horizontal lines) in the top left corner.
![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/27e2288f-e3a5-4c92-a2bd-454f9906d2bc)
3. Select BigQuery.


### Understanding the interface:

1. Navigation Panel:

- Explorer: This panel displays your projects, datasets, and tables in a hierarchical tree structure. Click on any element to access its contents. On the left side in the image.
- Jobs: This section shows your recent query jobs and their status. You can monitor their progress and view results here.In the bottom of the image ( it gives us the job information ,results, chart , json , execution details, execution graph )
- Favorites: Pin frequently used datasets or tables for quick access.( Star symbol against each dataset, table ) to pin it. 
- Search: Search for specific datasets, tables, or jobs. ( The search textbox is on the top)
![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/b190d882-75a1-493c-acec-f034c4e84666)


2. Main Content Area:

- Welcome Page: Provides an overview of BigQuery features and resources.
- Dataset/Table View: When you select a dataset or table, this area displays details like schema, location, and permissions.
- Query Editor: Write and execute SQL queries to analyze your data.
- Results View: Shows the results of your queries in a tabular format.
- Visualization Tools: Explore your data visually using charts and graphs.
![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/77282791-01f1-4743-b86e-66f2d5f00c38)


3. Toolbar:

- Create: Access options to create new datasets, tables, and queries.
- Query History: View previously executed queries.
- Settings: Configure your BigQuery preferences.
- Help: Find documentation and resources for BigQuery.
![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/ef5376bb-494c-4f9c-a860-962724dc998d)


### Loading Data into Bigquery 

1. Navigate to the project on the Navigation Panel under the explorer section. Click on "Create Data Set"
  ![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/399d1edf-3de3-452a-99e9-c9749d9905e7)

2. Create Dataset window will open on the right side
   
  ![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/e911a428-61ff-4b0c-8c24-610bd8942b59)


   Please consider following before creating the dataset 
   - Dataset names are case sesitive , similar names of the datset with different case can co exist.
   - Dataset location type and region can't be changed once set.
   - Always locate the datset in the same region as the external dataset or destination
   - Always choose default table expiration until you are working on a temporary table
   - The Created dataset will be seen under the project under the explorer

3. Create or Upload Table in the Dataset

   - Tables in the datset can be of different types
     a) Internal tables which are stored in the BigQuery
     b) External Tables which are stored in the Bucket,Google drive, Cloud SQL or Bigtable
     c) Views which are the virtual tables defined by the Bigquery query.

   - Several ways to load data into BigQuery
     a) Loading the data in batch in the csv , json or AVRO file.
     b) Saving the query results to a table
     c) Stream individual or batches of records into Bigquery.
     d) Load data from other services like google drive,google analytics etc.
  
  - Create table from the Dataset

![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/3582016e-4bf8-494a-bc6c-f0f9fe4792e8)

  - We can finally create the table by filling the details in the below page
    
![image](https://github.com/Saurav6789/Google-Big-Query-Guide/assets/45622711/7576ba97-8ce9-44a6-bd9a-503d7846da0d)


  Please note the following points 

  a) We can create an empty table,upload the table from google drive , BigTable , Amzaon s3 , cloud storage etc.
  
  b) Can use CSV, AVRO, JSON, Parquet or ORC files for new table.
  
  c) We can also specify the schema.
  
  d) Partitioning can be done to reduce the scan size , helpful for dates and integer ranges.
  
  e) Clustering can be done to reduce the scan size, sorting the data in storage , works best for strings.
  
  f) In the Advanced options , we can also append or overwrite to the existing table. 


  ## Data Structure Supported by Bigquery

  - INT64 :- Integers from -10^19 to 10^19. Only integer type.
  - FLOAT64 :- Real-valued numbers.
  - NUMERIC :- Real-valued numbers: use for precision.
  - BOOL :- Booleans. TRUE or FALSE (case insensitive).
  - STRING :- Variable-length Unicode characters.
  - TIMESTAMP :- Absolute point in time (incl timezone).
  - GEOGRAPHY :- A point set on the Earth’s surface.
  - Array :- An ordered list: [0,1,2,3,4]
  - STRUCTS :- A group of fields in order.


## Null Values in BigQuery 

Null Values in Bigquery represents missing values. They are not 0, nor empty strings: they have no value.Comparisons with NULL will always return NULL: your WHERE
clause will filter out those rows! If you want to check if a value is NULL or want to include them in your result set, use the IS operator.



  


