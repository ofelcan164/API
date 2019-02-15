Uploads
=======

The upload API is how you can add files to Image Relay. Files are uploaded to Image Relay through the creation of
upload jobs. And files are sent up in chunks.

Create Upload Job
-----------------

* `post /upload_jobs.json` will start an upload job. You'll need the id from this to upload files. Each upload job will
create *one* asset. Each file specified within the "files" array will be part of this asset. Files will be nested together.
If a jpg is supplied as one of the nested files, that will always be used to create the thumbnail preview for the asset.
If no jpg is provided a preview will still be generated from the file if it is possible.

```json
{
    "folder_id":"555",
    "file_type_id":"123",
    "prefix":"/create/new/sub_folder"
    "files":
        [   {
                "name":"my_file.dng",
                "size":"1234567890"
            },
            {
                "name":"my_file.jpg",
                "size":"12231796"
            }
        ]
    "terms":
        [
            {
                "term_id":"888",
                "value":"Copyright 2013"
            },
            {
                "term_id":"889",
                "value":"sunset over Lake Champlain"
            }
        ]
}
```

This will return `201 Created` if successful, as well as a json representation of the upload job:

```json
{
    "id":384,
    "created_at":"2013-02-07T21:07:36Z",
    "files":
        [
            {
                "id":395,
                "name":"my_file.dng",
                "size":1234567890
            },
            {
                "id":396,
                "name":"my_file.jpg",
                "size":12231976
            }
        ]
}
```

Create a File Chunk
-------------------

* `post /upload_jobs/384/files/395/chunks/1.json` uploads a file chunk. The last number is the chunk number. This is used,
to determine the order to reassemble the chunks on the server. So the next chunk would be `post /upload_jobs/384/files/395/chunks/2.json`.
The request body should be the binary data of the chunk. Make sure to set the Content-Length header. The Content-Type header should be `application/octet-stream`

Chunk size is up to you, up to 5 MB in size. If you attempt to upload a chunk larger than 5 MB you'll receive an error.

POST requests to the chunk endpoint will return the following response codes:

* 204: File upload chunk processed successfully, waiting for more file chunks for the complete file upload.
* 201: File upload chunk processed successfully and the file upload is complete
* 422: File upload chunk failed, please ensure your file chunk is 5MB or less and retry.

Once all files for an upload job have been uploaded, an asset will be created automatically on Image Relay.

With `curl`, here is an example:

```shell
curl --data-binary @chunk.bin \
       -u user:pass \
       -H 'Content-Type: application/octet-stream' \
       -H 'Content-Length: [chunk size in bytes]' \
       -H 'User-Agent: IR (example@imagerelay.com)' \
       https://api.imagerelay.com/api/v2/upload_jobs/384/files/395/chunks/1.json
```

