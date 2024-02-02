# 🏹 Tools in Azure

## Azure Cosmos DB

Fully managed NoSQL.

## Databricks&#x20;

Data analytic platform

## Spark&#x20;

Large scale SQL, batch processing, Stream processing, and machine learning.

## Azure Data Factory

Execute Transform , extract, and final load.&#x20;

## Azure Synapse Analytics

Provide big data engineering services



## IOT (Internet of Things)





### Azure Storage&#x20;

1. Azure Blob(Text and binary data)
2. Azure Files(Manage file shares)
3. Azure Queue(a messaging store for messaging between application components)
4. Azure Table(No sql and structured data)

**Azure Blob Store**(cheapest way if no need to query the data)

* REST APIs
* SDKs for Azure Storage
* Supported languages

You can use Azure Cloud Shell, Azure Powershell, Azure CLI.

### Data Ingest

1. Azure Data Factory
2. Storage Explorer
3. AzCopy tool
4. PowerShell
5. Visual Studio

When you upload a file more than 2GB, use PowerShell, Visual Studio. it also automatically split data over 200GB.

#### You can't query your data from Blob directly. you have to move it into Azure storage account, or data lake storage.

Azure storage account uses **Azure Resource Manager (Role based access contro**l) for all the data.

## Azure Data Lake Storage

It is Hadoop compatible data repository and can store any size or type data.

Data gen 1 can't upgrade to gen 2, and because it uses access control based on the role, so it is easy to control the data access.

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## Azure Cosmos DB

It supports some APIs:

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

&#x20;The benefit of Azure Cosmos DB

1. Uptime (99.999%)
2. Replication&#x20;

If there is a regional disaster, it will automatically copy over.&#x20;

3. Consistency.&#x20;

### Azure Blob Storage - Basic Information

For scenarios where there's no need to query data, **Azure Blob Storage** presents a cost-effective option:

* **Accessibility**: Access blobs using REST APIs or SDKs across various programming languages.
* **Integration Tools**: Utilize tools like Azure Cloud Shell, Azure Powershell, and Azure CLI to manage your storage.

#### Data Ingestion Methods

To move data into Azure Blob Storage, consider the following methods:

1. **Azure Data Factory**: For data integration service, orchestrating and automating data movement and data transformation.
2. **Storage Explorer**: A graphical tool to manage Azure Storage accounts and access your blobs.
3. **AzCopy**: A command-line utility designed to copy data to/from Azure Blob Storage, File Storage, and Table Storage.
4. **PowerShell**: Leverage Azure Storage PowerShell module commands for data transfer tasks.
5. **Visual Studio**: Integrate Azure storage solutions into your development environment for a streamlined experience.

**Large File Handling**

For files larger than 2GB:

* Opt for PowerShell or Visual Studio to handle uploads efficiently.
* These methods automatically handle the splitting of data chunks over 200GB.

**Data Querying Limitation**

To perform query operations on your blob data, it must first be moved to an Azure Storage account or Azure Data Lake Storage.

### Azure Data Lake Storage - Overview

Azure Data Lake Storage provides:

* **Hadoop Compatibility**: A scalable repository for big data analytics workloads.
* **Data Storage**: Ability to store large volumes of data in any format.
* **Data Security**: Utilize Azure Resource Manager and Role-Based Access Control (RBAC) to manage access to your data.

Note that Azure Data Lake Storage Gen1 cannot be upgraded directly to Gen2.

### Azure Cosmos DB - Features

Azure Cosmos DB is known for:

1. **High Availability**: Guarantees an uptime of 99.999%, ensuring data is always accessible.
2. **Global Replication**: In the event of a regional disaster, Azure Cosmos DB provides automatic failover to a replica.
3. **Consistency Levels**: Offers a range of consistency options to balance between performance and data accuracy.

## Azure Synapse Analytics

It supports distributed tables: [**hash**, **round-robin**, and **replicated**. ](#user-content-fn-1)[^1]

#### Distributed Table Types in Azure Synapse Analytics

**Hash-Distributed Tables**

Hash-distributed tables in Azure Synapse Analytics are designed to optimize query performance on large datasets by distributing rows across computing nodes using a deterministic hash function. When a hash-distribution column is selected, the value of that column is used to assign each row to a specific node, ensuring even data distribution and parallelized query execution.

**Round-Robin Distributed Tables**

Round-robin distributed tables offer a method of evenly distributing data across all computing nodes without the need for a distribution column. This approach is simple and efficient, especially when there is no obvious column to use for hashing. It ensures a balanced allocation of rows but might not provide the same query performance optimizations as hash-distributed tables for certain workloads.

**Replicated Tables**

Replicated tables are used when a table's entire dataset is required to be present on every compute node. This is beneficial for small lookup tables, as it avoids shuffling data across nodes during query execution, thereby improving performance. Because the same data is stored on every node, this type of distribution is not suitable for large tables.



### Feature of Azure Synapse

1. quickly run queries at scale
2. Use replicated tables for higher performance
3. Use distributed tables to tune performance.
4. Pay only for the computation you use. Pause or resume the compute layer.

in Synapse, you can use Polybase to do the work.&#x20;

#### PolyBase in Azure Synapse Analytics

**What is PolyBase?**

PolyBase is a technology that allows you to query non-relational data held in Azure Blob Storage or Azure Data Lake Storage using familiar SQL language. It combines and federates data across different data stores.

**Key Features of PolyBase**

* Integrates with Azure Data Lake and Azure Blob Storage.
* Allows the use of T-SQL queries to join structured and unstructured data.
* Supports the import and export of data between relational and non-relational data stores.
* Provides the ability to scale out queries using MPP (Massively Parallel Processing) architecture.

**Benefits of Using PolyBase**

* Simplifies data management by querying over multiple data sources as if they are a single source.
* Reduces the need for ETL processes by directly querying external data sources.
* Enhances performance for big data analysis within Azure Synapse Analytics.

**How to Use PolyBase**

To utilize PolyBase in Azure Synapse Analytics, configure an external data source, create an external file format, define an external table, and then query the data using regular SQL statements.

```sql
-- Example: Setting up a PolyBase Query
-- Step 1: Configure external data source
CREATE EXTERNAL DATA SOURCE MyAzureBlobStorage
WITH (
    TYPE = HADOOP,
    LOCATION = 'wasbs://[container]@[storageaccount].blob.core.windows.net',
    CREDENTIAL = MyAzureBlobStorageCredential
);

-- Step 2: Create an external file format
CREATE EXTERNAL FILE FORMAT MyFileFormat
WITH (
    FORMAT_TYPE = DELIMITEDTEXT,
    FORMAT_OPTIONS (FIELD_TERMINATOR = ',', USE_TYPE_DEFAULT = TRUE)
);

-- Step 3: Define an external table
CREATE EXTERNAL TABLE MyExternalTable (
    [Column1] INT,
    [Column2] NVARCHAR(50),
    ...
)
WITH (
    LOCATION='/data/',
    DATA_SOURCE= MyAzureBlobStorage,
    FILE_FORMAT= MyFileFormat
);

-- Step 4: Query the data
SELECT * FROM MyExternalTable;
```

Note: Replace `[container]`, `[storageaccount]`, and data types/schemas as necessary for your specific scenario.

[^1]: 
