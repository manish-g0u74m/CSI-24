# Azure Storage Account Guide

## Table of Contents

1. [Create a Storage Account](#create-a-storage-account)
2. [Explore Options](#explore-options)
3. [Upload and Access Blob](#upload-and-access-blob)
4. [Authentication Techniques](#authentication-techniques)
5. [Azure Storage Explorer](#azure-storage-explorer)
6. [Provision Access Keys](#provision-access-keys)
7. [Shared Access Signature](#shared-access-signature)
8. [Stored Access Policy](#stored-access-policy)
9. [Access Tiers](#access-tiers)
10. [Lifecycle Policy](#lifecycle-policy)
11. [Object Replication](#object-replication)
12. [File Share Functionality](#file-share-functionality)
13. [Azure File Sync](#azure-file-sync)

## Create a Storage Account

1. Go to the Azure portal.
2. Click on `Create a resource` and select `Storage account`.
3. Fill in the necessary details such as subscription, resource group, and storage account name.
4. Choose the performance and replication options.
5. Click `Review + create` and then `Create`.

## Explore Options

1. **Performance**: Standard vs. Premium.
2. **Replication**: LRS, ZRS, GRS, RA-GRS.
3. **Access tier**: Hot, Cool, Archive.
4. **Networking**: Public endpoint, Private endpoint.
5. **Data protection**: Soft delete, versioning.
6. **Encryption**: Microsoft-managed keys vs. Customer-managed keys.

## Upload and Access Blob

```python
# Install Azure storage blob library
pip install azure-storage-blob

from azure.storage.blob import BlobServiceClient, BlobClient, ContainerClient

# Connection string
connection_string = "your_connection_string"

# Create blob service client
blob_service_client = BlobServiceClient.from_connection_string(connection_string)

# Create a container
container_name = "mycontainer"
container_client = blob_service_client.create_container(container_name)

# Upload a blob
blob_name = "myblob"
blob_client = container_client.get_blob_client(blob_name)
with open("sample.txt", "rb") as data:
    blob_client.upload_blob(data)

# Download the blob
with open("downloaded_sample.txt", "wb") as my_blob:
    download_stream = blob_client.download_blob()
    my_blob.write(download_stream.readall())
```

## Authentication Techniques
### 1. Shared Key Authorization:
   - Use the access keys from the storage account.
### 2. Shared Access Signature (SAS):
   - Create and use SAS tokens for granular access control.
### 3. Azure Active Directory (AAD):
   - Integrate with AAD for identity-based access.

## Azure Storage Explorer
1. Download and install [Azure Storage Explorer](https://azure.microsoft.com/en-us/products/storage/storage-explorer/).
2. Sign in to your Azure account.
3. Access your storage account and perform operations like upload, download, delete, etc.

## Provision Access Keys
1. Go to your storage account in the Azure portal.
2. Navigate to `Access keys`.
3. Copy the Key1 or Key2 and use it in your connection string.

## Shared Access Signature
1. Go to your storage account in the Azure portal.
2. Navigate to `Shared access signature`.
3. Generate a SAS token with required permissions and expiry time.
4. Use the SAS token to access resources.

## Stored Access Policy
1. Go to your container in the Azure portal.
2. Navigate to `Access policy`.
3. Create a policy with required permissions and expiry.
4. Associate the policy with your SAS token.

## Access Tiers
1. **Hot**: Frequently accessed data.
2. **Cool**: Infrequently accessed data with lower storage costs.
3. **Archive**: Rarely accessed data with the lowest storage cost.

## Lifecycle Policy
1. Go to your storage account in the Azure portal.
2. Navigate to `Lifecycle Management`.
3. Create a rule to move blobs between access tiers or delete them based on conditions.

## Object Replication
1. Go to your storage account in the Azure portal.
2. Navigate to `Object replication`.
3. Configure replication rules between source and destination accounts.

## File Share Functionality
1. Go to your storage account in the Azure portal.
2. Navigate to `File shares`.
3. Create a new file share and upload files.

## Azure File Sync
1 .Set up an Azure File Sync service in the Azure portal.<br>
2. Register your on-premises server with the sync service.<br>
3. Create a sync group and add the file share and server endpoint.<br>


<br>
-> This Markdown file provides a structured guide for working with Azure Storage accounts, covering creation, configuration options, blob operations, authentication techniques, tools like Azure Storage Explorer, access keys, shared access signatures, access policies, access tiers, lifecycle policies, object replication, file share functionality, and Azure File Sync. Adjust the placeholders (`your_connection_string`, etc.) with your actual values when implementing these steps.

