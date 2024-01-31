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

&#x20;

