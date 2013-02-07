Uploads
=======

*THIS IS INCOMPLETE DO NOT USE IT YET*

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
                "name":"test.jpg",
                "size":12231976
            }
        ]
}
```