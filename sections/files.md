Files
=====

Files - the reason you're using Image Relay. Here's how you get at them via the API.

Get Files
---------

* `GET /folders/555/files.json` returns all the files in the specified folder

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding &page=2 to the query, then &page=3 and so on. The 555 in the example above should be replaced with the folder ID number.

Additionally, there is a filter you can add as a parameter, upload_after, which will filter the files returned to only those tht have been uploaded after that date. The format of the parameter should be: "YYYY-MM-DD HH:MM:SS GMT+00:00". You can leave off the timezone information if you are using UTC time, you can leave off time if you want it filtered from the beginning of the day specified (e.g. YYYY-MM-DD).

Example (url encoded):
`GET /folders/555/file.json?uploaded_after=2014-06-10%2001:00:00%20GML%2B00:00`

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

* `GET /files/1234` returns the specified file.

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

