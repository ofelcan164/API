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

Additionally, there is a filter you can add as a parameter, upload_after, which will filter the files returned to only those tht have been uploaded after that date. The format of the parameter should be: "YYYY-MM-DD HH:MM:SS GMT+00:00". You can leave off the timezone information if you are using UTC time, you can leave off time if you want it filtered from the beginning of the day specified (e.g. YYYY-MM-DD).

Example (url encoded):
`GET /folders/555/files.json?uploaded_after=2014-06-10%2001:00:00%20GML%2B00:00`

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
      ]
  }
```

Upload File From URL
-----------

* `POST /files.json` returns `201 OK` if the file was uploaded successfully. 

We will respond with information about the file uploaded in the response body.  A filename, a folder_id for the folder the file will be uploaded to, a file_type_id, terms, and a url where the file will be downloaded from are required.  Metadata terms should be in the form of a hash, with a term_id and a value.  If you don't want to set any metadata on upload terms can be nil.

```json
{
  "filename":"Example.jpg",
  "folder_id":"12397",
  "file_type_id":"149",
  "terms":{"term_id":"", "value":""},
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
      "value": ""
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
  ]
}
```

Move File
-------------

* `POST /files/555/move` will move the file to the specified folder ids, removing it from any other folders.

```json
{
  "folder_ids": [ 123456, 8877899 ]
}
```

Copy File
-------------

* `POST /files/555/copy` will copy the file to the specified folder ids, leaving it in any existing folders.

```json
{
  "folder_ids": [ 123456, 8877899 ]
}
```



