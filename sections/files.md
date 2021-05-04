Files
=====

Files - the reason you're using Image Relay. Here's how you get at them via the API.

Get Files
---------

* `GET /folders/555/files.json` returns all the files in the specified folder

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding &page=2 to the query, then &page=3 and so on. The 555 in the example above should be replaced with the folder ID number.

You may limit files returned by keyword using a query parameter, for example:
`/api/v2/folders/123456/files.json?query=dogs`

To search all the files in the archive by keyword via the API, obtain the root folder id of the archive via API (`GET /folders/root.json`), this ID will never change, then use this call:
`/api/v2/folders/{{ replace with root folder id}}/files.json?query=dogs&recursive=true`

The following filters/query parameters can be used when requesting a file's folders:

`uploaded_after` will filter the files returned to only those that have been uploaded after that date. The format of the parameter should be: "YYYY-MM-DD HH:MM:SS GMT+00:00". You can leave off the timezone information if you are using UTC time, you can leave off time if you want files filtered from the beginning of the day specified (e.g. YYYY-MM-DD)

`updated_after` will filter the files returned to only those that have been updated/modified after that date. The date/time should be formatted the same as upload_after.

`file_type_id` will filter the files returned to only those that have the asset profile/file type id of the supplied parameter

*Note: The above filter parameters can be combined*

Example urls (url encoded):

`GET /folders/555/files.json?uploaded_after=2014-06-10%2001:00:00%20GML%2B00:00`

`GET /folders/555/files.json?updated_after=2014-06-10`

`GET /folders/555/files.json?file_type_id=149`

`GET /folders/555/files.json?file_type_id=149&updated_after=2014-06-10`

```json
[
  {
    "id":2222,
    "filename":"basic_perm_icon.png",
    "created_at":"2013-05-20T12:58:07Z",
    "updated_on":"2013-05-20T13:03:36Z",
    "size":7358,
    "width":101,
    "height":101,
    "content_type":"image/png",
    "user_id":405,
    "deleted":null,
    "deletion_date":null,
    "delete_user_id":null,
    "file_type_id":149,
    "terms":
      [
        {
          "term_id":70497,
          "value":" "
        },
        {
          "term_id":70498,
          "value":" "
        },
        {
          "term_id":70499,
          "value":" "
        },
        {
          "term_id":70500,
          "value":" "
        }
      ],
      "tags":
      [
        {
          "tag_id":12645,
          "value":"Sports"
        },
        {
          "tag_id":765987,
          "value":"Marketing"
        }
      ]
  },
  {
    "id": 1234,
    "filename":"grey_lock_icon.png",
    "created_at":"2013-05-20T12:58:05Z",
    "updated_on":"2013-05-20T13:03:33Z",
    "size":2974,
    "width":15,
    "height":19,
    "content_type":"image/png",
    "user_id":405,
    "deleted":null,
    "deletion_date":null,
    "delete_user_id":null,
    "file_type_id":149,
    "terms":
      [
        {
          "term_id":70493,
          "value":" "
        },
        {
          "term_id":70494,
          "value":" "
        },
        {
          "term_id":70495,
          "value":" "
        },
        {
          "term_id":70496,
          "value":" "
        }
      ],
    "tags":
      [
        {
          "tag_id":12645,
          "value":"Sports"
        },
        {
          "tag_id":765987,
          "value":"Marketing"
        }
      ]
  }
]
```

Get File
--------

* `GET /files/1234.json` returns the specified file, where 1234 is the unique of the file.

```json
  {
    "id": 1234,
    "filename":"grey_lock_icon.png",
    "created_at":"2013-05-20T12:58:05Z",
    "updated_on":"2013-05-20T13:03:33Z",
    "size":2974,
    "width":15,
    "height":19,
    "content_type":"image/png",
    "user_id":405,
    "deleted":null,
    "deletion_date":null,
    "delete_user_id":null,
    "file_type_id":149,
    "terms":
      [
        {
          "term_id":70493,
          "value":" "
        },
        {
          "term_id":70494,
          "value":" "
        },
        {
          "term_id":70495,
          "value":" "
        },
        {
          "term_id":70496,
          "value":" "
        }
      ],
    "tags":
      [
        {
          "tag_id":12645,
          "value":"Sports"
        },
        {
          "tag_id":765987,
          "value":"Marketing"
        }
      ]
      
  }
```

Upload File From URL
-----------

* `POST /files.json` returns `201 OK` if the file was uploaded successfully. 

We will respond with information about the file uploaded in the response body. 

A filename, a folder_id for the folder the file will be uploaded to, a file_type_id, terms, and a url where the file will be downloaded from are required.  

Metadata terms should be in the form of a hash, with a term_id and a value.  If you don't want to set any metadata on upload, terms can be nil. 

Keyword ids are optional and should be an array if included.

```json
{
  "filename":"Example.jpg",
  "folder_id":"12397",
  "file_type_id":"149",
  "terms": [
    {
      "term_id": "75206", 
      "value": "hello world"
    }
  ],
  "keyword_ids": ["1"],
  "url":"http://www.imagerelay.com/test_image.jpg"
}
```
We will return a representation of the uploaded file.

```json
{
  "id": 242802,
  "filename": "test.jpg",
  "created_at": "2015-06-03T12:58:43Z",
  "updated_on": "2015-06-03T12:58:43Z",
  "size": 0,
  "width": null,
  "height": null,
  "content_type": "image/jpeg",
  "user_id": 405,
  "deleted": null,
  "deletion_date": null,
  "delete_user_id": null,
  "expires_on": null,
  "expiring_user_id": null,
  "file_type_id": 149,
  "short_lived_thumbnail": "/static/processing.png",
  "terms": [
    {
      "term_id": 75206,
      "value": "hello world"
    },
    {
      "term_id": 75207,
      "value": ""
    },
    {
      "term_id": 75208,
      "value": ""
    },
    {
      "term_id": 75209,
      "value": ""
    },
    {
      "term_id": 75210,
      "value": ""
    },
    {
      "term_id": 75211,
      "value": ""
    }
  ],
  "tags": [
    {
      "tag_id": "1",
      "tag_value": "A Tag"
    }
  ]
}
```

Update File Keywords
-------------

* `POST /files/555/terms` will update the metadata keyword terms of the file specified.

Parameters:
  terms - an array of term ids and values to update. 
  overwrite - if true, it will overwrite the entire value for that term, if false, it will append the value to any existing metadata already present in that term field.

```json
{
  "terms": [
    { 
      "term_id": 1234,
      "value": "The quick brown fox"
    },
    {
      "term_id": 5678,
      "value": "All rights reserved"
      
    }
  ],
  "overwrite": true
}
```

Update File Tags
-------------

* `POST /files/555/tags` will update the metadata keyword terms of the file specified.

Parameters:
  tags - contains a list of tag ids to both add and remove from the asset. 

```json
{
  "tags": 
    { 
      "add_ids": [ 1234, 4566 ],
      "remove_ids": [ 65489, 78976 ]
    }
}
```

Delete File
-------------

* `DELETE /files/555` will delete the file specified by id.

Returns `204 No Content` if successful


Move File
-------------

* `POST /files/555/move` will move the file to the specified folder ids, removing it from any other folders.

```json
{
  "folder_ids": [ 123456, 8877899 ]
}
```

Synced File / Copy
-------------

* `POST /files/555/synced_file` or `POST /files/555/copy` will create a synced file within the specified folder ids, leaving it in any existing folders.

 Synced Files let you have the exact same file in multiple folders. When you make a change to any Synced File, that change applies to all instances of the Synced File.
 
 We will be removing the `/files/555/copy` endpoint soon - please start using /synced_file in your integrations.

 The JSON body should contain an array of folder ids

```json
{
  "folder_ids": [ 123456, 8877899 ]
}
```

Duplicate File
-------------

* `POST /files/555/duplicate` will create a duplicate of the file in a single destination folder. This duplicate behaves as a completely new file and is completely separate from the original file.

 You can choose to copy all metadata, tags/keywords, and IPTC fields or not. Here's an example JSON body
 
 If you choose to not copy metadata (`"should_copy_metadata": false`) - the copied file will get the destination folder's default asset profile
 
 ```json
 {
	"folder_id": 123456,
	"should_copy_metadata": false
 }
 ```
 *Please note: there can only be a single destination `folder_id`, not an array of ids*
 
Asset Thumbnail
-------------

* `POST /files/555/thumbnail?file_name=image.png` will update the asset thumbnail.

Make sure that the header `Content-Type: application/octet-stream` is present and the request body is the binary file data. The total file size must be 5Mb or less. Only JPG and PNG image types are supported. 

A `file_name` parameter is required in the query string. Make sure the `file_name` includes an extension otherwise you will receive an error. 

Here is an example curl request that illustrates how to use the API. 

```shell
curl -u "user:pass" \
  -X "POST" \
  -H "User-Agent: MyApp (you@example.com)" \
  -H "Content-Type: application/octet-stream" \
  --data-binary "@image.png" \
 https://api.imagerelay.com/api/v2/files/555/thumbnail?file_name=image.png
```
 

(DEPRECATED) Update Version 
---------------

This endpoint has been deprecated. Use the "Chunked Update Versions" endpoint instead. 

* `POST /files/555/version` will update the underlying file for the file specified with the id (in example id=555).
 The request body should be the binary data of the new file. Make sure to set the Content-Length header. The Content-Type header should be application/octet-stream, the maxium file size supported for this update is 1 GB. 
 
 With `curl`, here is an example:

```shell
curl --data-binary @myfile.jpg \
       -u user:pass \
       -H 'Content-Type: application/octet-stream' \
       -H 'User-Agent: IR (example@imagerelay.com)' \
       https://api.imagerelay.com/api/v2/files/555/version.json
```


Chunked Update Versions
---------------

To update an asset you will need to upload your file in chunks. Each chunk must be under 5Mb. 

File chunks are grouped together using a v4 UUID. 

### Obtaining a v4 UUID


`POST /api/v2/files/555/versions` will return a JSON response with a valid v4 UUID. Use this when when uploading chunks. 

* `{"uuid": "A v4 uuid will be here" }`

_Please note that "versions" is pluralized in the path_

### Uploading Chunks

* `POST /api/v2/files/555/versions/[v4 uuid]/chunk/[chunk number]` to upload a chunk. 

The request body should be the binary data of the file chunk and the Content-Type should be `application/octet-stream`. 

The chunk number in the path is used for ordering chunks when assembling the final file.

You will receive a `204 no content`, http status code when the chunk has uploaded successfully.

### Completing the Upload

After all chunks have uploaded successfully you will have to tell the API that the file is ready for processing. 

* `POST /api/v2/files/555/versions/[v4 uuid]/complete` will queue your file for processing. 

This endpoint requires a JSON object in the request body with the Content-Type set to `application/json`. 

The JSON body you post must contain two attributes, a `file_name` and `chunk_count`. 

```json
{
"file_name": "image.png",
"chunk_count": 2
}
```

The `file_name` used here will replace the name of the asset. Also make sure that the `file_name` has an extension. 

You will receive a `201 created`, http status code on success. 

### Example 

Here is an example using curl to create a new version of an asset.

Step 1: Request a valid v4 UUID from the API

```
curl -u "user:pass" \
  -X POST \
  -H 'User-Agent: MyApp (you@example.com)' \
  "https://api.imagerelay.com/api/v2/files/555/versions"
```

Step 2: Start uploading chunks. _Please note the chunk number at the end of the path corresponds to the chunk being uploaded_

```
# chunk 1
curl -u "user:pass" \
  -X POST \
  -H 'Content-Type: application/octet-stream'  \
  --data-binary "@chunk1" \
  "https://api.imagerelay.com/api/v2/files/555/versions/abc-def-ghi/chunk/1" 

# chunk 2
curl -u "user:pass" \
  -X POST \
  -H 'Content-Type: application/octet-stream' \
  --data-binary "@chunk2" \
  "https://api.imagerelay.com/api/v2/files/555/versions/abc-def-ghi/chunk/2" 
```

After all chunks have uploaded you may now hit the complete endpoint to start processing the file.

```
curl -u "user:pass" \
  -X POST \
  -H 'Content-Type: application/json' \
  -d '{"file_name":"image.png", "chunk_count":2}' \
  "https://api.imagerelay.com/api/v2/files/555/versions/abc-def-ghi/complete"

```
