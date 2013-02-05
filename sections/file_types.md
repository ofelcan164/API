File Types
==========

Each file in Image Relay is assigned a file type. Different file types have different sets of metadata associated with them.

Get File Types
--------------

* `GET /file_types.json` will return all the file types for the account.

```json
[
  {
    "name":"Action A1",
    "description":"NaN",
    "created_on":"2008-05-18T20:16:52Z",
    "updated_on":"2013-01-07T17:06:14Z",
    "id":149,
    "terms":
      [
        {
          "name":"Keywords",
          "position":1,
          "meta_name":"",
          "display_in_download":null,
          "created_on":"2012-06-08T12:44:38Z",
          "updated_on":"2012-06-08T12:44:38Z",
          "id":1378
         },
         {
           "name":"Copyright",
           "position":2,
           "meta_name":"",
           "display_in_download":null,
           "created_on":"2012-06-08T12:44:38Z",
           "updated_on":"2012-06-08T12:44:38Z",
           "id":1379
         },
      ]
  },
  {
    "name":"Meta Data",
    "description":"Testing Excel",
    "created_on":"2009-05-06T10:48:00Z",
    "updated_on":"2009-05-06T12:43:30Z",
    "id":194,
    "terms":
      [
        {
          "name":"Title",
          "position":1,
          "meta_name":"Title",
          "display_in_download":null,
          "created_on":"2009-05-06T10:48:00Z",
          "updated_on":"2009-05-06T10:48:00Z","id":1179
        }
      ]
  }
]
```

Get File Type
-------------

* `GET /file_types/555.json` will return the specified file type.

```json
{
 "name":"Action A1",
 "description":"A File Type",
 "created_on":"2008-05-18T20:16:52Z"
 ,"updated_on":"2013-01-07T17:06:14Z",
 "id":149,
 "terms":
   [
     {
       "name":"Keywords",
       "position":1,
       "meta_name":"",
       "display_in_download":null,
       "created_on":"2012-06-08T12:44:38Z",
       "updated_on":"2012-06-08T12:44:38Z","id":1378
     },
     {
       "name":"Copyright",
       "position":2,"meta_name":"",
       "display_in_download":null,
       "created_on":"2012-06-08T12:44:38Z",
       "updated_on":"2012-06-08T12:44:38Z",
       "id":1379
     }
   ]
}
```
