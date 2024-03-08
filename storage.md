Azure Storage, Blob Storage



●	Azure Storage offers the following options



○	Blob Storage: Massively scalable object store for data objects. It is suitable for

■	HTTP based file retrieval



■	Distributed file access



■	Media Streaming



■	Log and archival purposes



■	Data analysis



○	File Storage: File system storage for the cloud. This is ideal for

■	Replacing or supplementing on-premises storage



■	“Lift and Shift application”



■	Shared application settings



■	Development purposes



○	Table Storage: This is a NoSQL based storage system. It can be used for

■	Storage of high volume structured data



■	Storing datasets without complex joins and foreign keys



■	Querying data with clustered indices



■	Accessing data using the OData protocol and LINQ queries



○	Storage Queue: Messaging storage for reliable messaging. This is used for

■	Storing a list of asynchronous tasks



■	Passing messages from an Azure web role to a worker role



●	The different storage options available are



○	Standard: Uses Magnetic drives and is best for bulk storage or infrequently accessed data



○	Premium : Uses Solid State drives and is best used for IO intensive applications, like databases, and Azure Virtual Machine drives.



●	The following replication options are available



○	Locally Redundant Storage (LRS): The replicas are created in the same datacenter as the original



○	Geo-Redundant Storage(GRS): The replicas are created in a different geographical region



○	Read-Access Geo-Redundant Storage(RA-GRS): The replicas are created in a different geographical region, but with reduced performance and in read-only mode.



●	The NuGet Package provides the APIs for the SDKs provided by Microsoft.

 






**Azure Storage Options: Blob Storage**

Azure Blob Storage is a scalable object store designed to store large amounts of unstructured data. Here's a detailed explanation along with deployment steps on Azure:

**Deployment Steps:**

1. **Sign in to Azure Portal**: Go to the Azure portal (https://portal.azure.com) and sign in with your Azure account.

2. **Create a Storage Account**: Navigate to the Storage Accounts service and click on "Add" to create a new storage account. Choose a unique name, select the desired performance (Standard or Premium), replication option (LRS, GRS, RA-GRS), and other settings according to your requirements. Click on "Review + create" and then "Create" to provision the storage account.

3. **Access Keys**: Once the storage account is created, go to its settings and navigate to the "Access keys" section. Note down one of the access keys as you will need it to authenticate your application with the storage account.

4. **Create a Blob Container**: Inside your newly created storage account, create a blob container. Blob containers are logical containers for organizing and managing blobs. You can create multiple blob containers to separate different types of data.

5. **Upload Blobs**: Use Azure Storage Explorer, Azure CLI, or your application code to upload blobs (files) to the blob container. Blobs can be of different types, such as block blobs, append blobs, or page blobs, depending on your requirements.

6. **Access Blobs**: Access your blobs programmatically using the Azure Blob Storage SDK for your preferred programming language. You can perform operations like uploading, downloading, listing, and deleting blobs.

**Features of Blob Storage:**

- **HTTP-based file retrieval**: Blobs can be accessed via HTTP endpoints, making it easy to integrate with web applications and services.

- **Distributed file access**: Blob Storage supports distributed access to stored blobs, allowing multiple clients to concurrently access and modify data.

- **Media Streaming**: It's commonly used for storing media files such as images, videos, and audio, which can be streamed directly to clients.

- **Log and archival purposes**: Blob Storage is suitable for storing log files, archival data, backups, and other types of data that require long-term retention.

- **Data analysis**: It can be used as a data lake for storing large datasets used for analytics and data processing tasks.

**Replication Options:**

- **Locally Redundant Storage (LRS)**: Copies data synchronously within a single datacenter, providing high durability and availability within that region.

- **Geo-Redundant Storage (GRS)**: Replicates data asynchronously to a secondary region, providing data redundancy and disaster recovery capability across geographical regions.

- **Read-Access Geo-Redundant Storage (RA-GRS)**: Similar to GRS but also allows read access to the replicated data in the secondary region, although with potentially reduced performance compared to the primary region.

**JSON Example:**

```json
{
  "storageAccount": {
    "name": "exampleStorageAccount",
    "type": "BlobStorage",
    "performance": "Standard",
    "replication": "GRS",
    "containers": [
      {
        "name": "exampleContainer1",
        "access": "Private"
      },
      {
        "name": "exampleContainer2",
        "access": "Public"
      }
    ]
  }
}
```

This JSON example demonstrates creating a Blob Storage account with GRS replication and two blob containers, one with private access and the other with public access.

