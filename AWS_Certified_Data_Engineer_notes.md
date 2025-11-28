# AWS Certified Data Engineer Associate
These notes are from teh Udemy course found at: https://www.udemy.com/course/aws-data-engineer/?kw=AWS+Certified+Data+Engineer&src=sac&couponCode=CP251120G2V2

Sections covered are:
- **Data Engineering Fundamentals**
- **Storage**
- **Database**
- **Migraton and Transfer**
- **Compute**
- **Containers**
- **Analytics**
- **Application Integration**
- **Security, Identity, and Compliance**
- **Networking and Content Delivery**
- **Management and Governance**
- **Machine Learning**
- **Developer Tools**
- **Everything Else**

Let's get into it

# Data Engineering Fundamentals
This section is a review of some data engineering topics that are questioned on the exam.

## Types of Data
There are three types of data:

### Structured Data
This is data that is organized in a defined manner or schema, typically found in relational databases.

Characteristics are:
- Easily queriable
- Organized in ros ndd columns
- Has a consistent structures

Some examples are:
- Database tables
- CSV files with consistent columns
- Excel spreadsheets

### Unstructured Data
Tis is data that does not have a predefined scema or structure.

Its caracteritic are:
- Not easily queriable without preprocessing
- May come in various formats

And some examples are:
- Text files without a fixed format
- Video and audio files
- Images
- Emails and word processing documents

### Semistructured Data
This is data that is in between structured and unstructured. This is data not as organized as structured data but has some level of structure in form of tags, hierarcies or other patterns.

Its characteristics are:
- Elements might be tagged or categorized in some way
- It's more flexible than structured data but not as chaotic as unstructured data

And some examples are:
- XML and JSON files
- Email headers
- Log files with varied formats

## Properties of Data
There are three ain properties of data: the three V's

**Volume**: refers to the amount or sze of data that organizations are dealing with at any given time. Ots characteristics are:
    - Ranges from GB to PB or more
    - Comes with challenges in storing, processing and analyzing high volumes of data

**Velocity**: refers to the speed at which new data is generated, collected and processed. Some characteristics are:
    - High velocity requires real-tme or near-real-time processing capabilities
    - Rapid ingestion and processing can be critical for certain applications

**Variety**: refers to the different types, structures and sources of data (structured or unstructured, formats and sources).

## Data Warehouses vs Data Lakes
Let's compare these two options of storage so that you can hoose the best option in each scenrio

### Data Warehouses
A **Data Warehouse** is a centralized repository optimized for analysis were data from different sources is stored n a structured format.

Characteristics:
- Designed for complex queries and analysis
- Data is cleant, transformed and loaded (ETL process)
- Typically uses a star or snowflake schema
- Optimized for read-heavy operations

Some examples are:
- **Amazon Redshift**
- **Google Big Query**
- **Azure SQL Data Warehouse**

### Data Lakes
A **Data Lake** is a storage repository that holds a vast amount of raw data in its native format that includes structured, unstructured and semi-structured.

It's characteristics are:
- Can tore arge volumes of raw data without predefined schema
- data is loaded as-is, o need for preprocessing
- Supports batch, real-time and stream processing
- Can be queried for data transformations or exploratio purposes

Some examples are:
- **S3**: Amazon Smple Storage Servie when used as data lake
- **Azure Data Lake Storage**
- **Hadoop Distributed File System**

### Data Wareouse vs Data Lake
- **Schema**:
    - Data Warehouse has a schema-on-write policy (predefined scema before writing the data). ETL
    - Data Lake has a shcema-on-read policy (schema is defined at the time of reading the data). ELT
- **Data Types**:
    - Data Warehouse contains primarily structured data
    - Data Lake can contain any type of data
- **Agility**:
    - Data Warehouse is less agile due to predefined schema (if you need to change the schema, there's a costy migration)
    - Data Lake is more agile as it accepts raw data without a predefined structure
- **Processing**:
    - Data Warehouse uses ETL
    - Data Lake uses ELT
- **Cost**:
    - Data Warehouse tends to e more expensive because of the optimizations needed for complex queries
    - Data Lake is a more cost effective storage solution, but costs can rise when processing large amounts of data

### Choosing between Data Warehouse and data Lake
***Use a Data Warehoue when***:
- You have structured data sources and know the schema upfront
- If you require fast and complex queries
- If data integration from different sources is essential
- If business inteligence and analytics are the primary use cases

***Use Data Lake when***:
- When you have a mixture of data types
- You need a scalable and cost-effective solution to store massive amounts of data
- When your future needs for data are uncertain and want flexibility in storage and processing
- For advanced analysitcs, machine learning or data discovery

### Data Lakehouses
A **Data Lakehouse** is a hybrid data architecture that combines the best features of data lakes and data warehouses, aiming to provide the performance, reliability and capabilities of a data warehouse while maintaining the flexibility, scale and low-cost storage od data lakes

Its characteristics are:
- Supprts both structured and unstructured data
- Allows for schema-on-write and schema-n-read
- Provides capabilities for both detailed analytics and machine learning tasks
- Typically built on top of cloud or distributed architectures
- Benefits from technologies like Delta Lake, which bring ACID transactions to big data

Some examples are:
- **AWS Lake Formation**: uses Redsift Spectrum to query data from S3
- **Delta Lake**
- **Databricks Lakehouse Platform**
- **Azure Synapse Analytics**

## What is a "Data Mesh"?
A **Data Mesh** is a architecture style with rules for governance and ownnership.

The idea behind is that each team is the owner of its data and the different teams share the data of each domain between each other.

There's  federated governance with some cental standards. Each team uses if own tools.

## Managing and Orchestrating ETL Pipelines
**ETL** (Extract, Transform, Load) is a process used to move data from source systems into a data warehouse:

- **Extract**: in this stage you retrieve data from source systems wich can be of any type; ensure data integrity correctness during the extraction phase; and this can be done in real-time or in batches, depending on requirements
- **Transform**: here the data extracted is converted into a format suitable for the target data warehouse. It can involve several operations (data cleansing, data enrichment, format changes, aggregations or computations. encoding and decoding, andling missing values...)
- **Load**: consists in moving the transformed data into the datrget data warehouse or data repository. Can be done in batches or streaming. 

The main tool for ETL and ELT that is AWS native is **AWS Glue**. Other orchestration services are:
- EventBridge
- Amazon Managed Workflows for Apache Airflow, AWS
- AWS step Functions
- Lambda
- Glue Workflows

## Other topics
The rest of the topics are too introductory and are skipped in these notes. You may check them at the course itself.

# Data Storage
This section covers the AWS tools for storage of data in the cloud

## Amazon S3
**S3** is one of the main building block sof AWS. ***It is advertised as "infinitely scaling" storage.***

Some use cases are:
- Backup and storage
- Disaster recovery
- Archive data
- Hybrd Cloud Storage
- Application Hosting
- Media Hosting
- data Lakes and big data analytics
- Software delivery
- Static website

### Buckets
Amazon S3 stores data in **Buckets** (directories). Nuckets must have a global unique name across all regions.

However, buckets are defined at the region level.

S3 looks like a global service, but buckets are created in a regions!

### Objects
**Objetcs** in S3 is the name used to refer to files stored in S3. Each object has a ***key*** composed by a prefix and an object name. The prefix refers to the "folder" where the file is stored. 

***Note that S3 does not actually uses folders***, this is merely a UI option, but internally objects are referred by index. By using the same prefix for several objects you are not really storing them in the same folder.

The value of an object is its content:
- Maixmum size of an objetc is 5TB (500GB)
- Files bigger than 5GB require mult-part upload
- Metadata: 
- Tags: to identify files with natural language
- Version ID: a file can be refresed, deleted... this version id indicates the in-use version of the file

### S3 Security
There are several options and security levels available in S3:
- User-based: by implementing IAM policies we can define which API calls should be allowed for a specific user from IAM
- Resource-Based:
    - Bucket Policies: these are bucket-wide rules from the S3 console, allowing cross account
    - Object Access Control List (ACL): finer grain
    - Bucket Access Control List
- Encryption: using encryption keys to secure the content of an object

#### S3 Bucket Policies
S3 Bucket policies are implemented using JSON files: these are JSON files containing the details of the scurity rules:
```json
{
    "Version":"2013-10-17",
    "Statement":[
        {
            "Sid":"Publicread",
            "Effect":"Allow",
            "Principal":"*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource":[
                "arn:aws:s3:::examplebucket"
            ]
        }
    ]
}
```

The JSON contains the following details:
- The resources to be affected (buckets and objects)
- The effect of the rule (Allow or Deny)
- The actions: a set of API calls to Allow or Deny
- The principal: the account or user to apply the poliy to

You should use S3 bucket policies for:
- Grant public access to the bucket
- Force objects to be encrypted at upload
- Grant access to another account (Cross Account)

### S3 Versioning
S3 allows file versioning at the bucket level. ***This is not enabled by detault, you need to enable it***. Files uploaded before enabling versioning will have a NULL version id.

A new version of the object with the same key but with a different version id is available in the S3 Bucket. And rollback is also available through this versioning.

To roll back, you can simply delete the file containing the version.

Now, when you delete a file for good, you are actually deleting with a marker, so that it is still stored with a new version id. If you delete the version of the delete marker, the file will be restored.

### S3 Replication
There are two types of replication:
- **Cross Region Replication**: creates an extra bucket n another region
- **Same Region Replication**

***Buckets can be defined in different AWS accounts***
The requirements are:
- To implement relication, the buckets must have versioning enable
- Buckets must be given proper IAM permissions to the other S3 bucket

Some use cases are:
- CRR: Compliance, providing lower latency, data replication accorss accounts
- SRR: log aggregation, live replication between production and test accounts.

***Replication will automatically happen only for files created after the enabling of replication***. For previous files you need to use **S3 Batch Replication**, which replicates existing objetcs as well as files whose replication failed.

Also, for delete operations:
- Delete markers can be replicated from source to target
- Deletions with a version ID are not replciated

Finally, chain of replication is not allowed: if bucket 1 replicates to bucket 2 and bucket 2 replicates to bucket 3, objects from bucket 1 will NOT replicate to bucket 3.