[Home](../README.md)

# Blob storage connectors
https://docs.resco.net/wiki/Blob_storage_for_Resco_Cloud
 
# Problem
![actual situation](actualSituation.png)
Blobs are stored directly in the database in SQL Server database as a regular table field (nvarchar(max) or varbinary(max) type). It is expensive and it slows down some processes.
Create connectors for different storage providers, so every customer can setup his own, alternatively can use the defualt one, which will be maintained by Resco.
Part of the solution should be ability to migrate existing blobs to the external storage. 
Synchronization between server and the mobile app must not be affected by these changes.

# Solution
![solution diagram](solutionDiagram.png)

* User is able to setup external blob storage on Resco Cloud.
* Authentication oAuth2.0
* Plugins/Connectors implements interface:

```c#
public interface IXRMBlobStorage : IDisposable
{
	int MinBlobSizeToUpload { get; }
	
	bool Backup(XRMBlobStorageBackupRequest request);
    bool Copy(XRMBlobStorageCopyRequest request);
    void Delete(XRMBlobStorageFileTransferRequest request);
	Stream Download(XRMBlobStorageFileTransferRequest request);
    long GetSize(XRMBlobStorageFileTransferRequest request);
    bool Move(XRMBlobStorageMoveRequest request);
    bool Restore(XRMBlobStorageRestoreRequest request);
	bool Upload(XRMBlobStorageUploadRequest request);
}
```

### Supported storages
* Azure Storage
* Amazon S3
* SharePoint
* OneDrive

### Supported cases
* a) migrate existing blobs from database to external storage
* b) use external storage during synchronization
* c) migrate blobs from one external storage to the different external storage

### Performance comparison of plugins/storages
* Upload - time in ms per record
* Download -1000 x 422KB + 50 x 3.83MB
 
|  | amazon | azure | onedrive | sharepoint  |
|--|--|--|--|--|
| upload - 3.83MB |1845 ms  | 4124 ms | 2475 ms | 2525 ms |
| upload - 422KB |593 ms  | 627 ms  | 640 ms  | 581 ms |
| download | 228 s | 155 s | 188 s |  168 s |

* Results:

-It seems, that amazon has the best performance during uploading of "larger" files.

-Azure has the worst uploading times, but the best times during downloading

[->Next: Computed Columns in SQL Server](../computedColumns/readme.md)