Folder Links
===========

Allows you to retrieve information about, create, or destroy folder links.
Folder links provide a portable and easy view experience of your folders. Allowing someone to upload to a folder requires an upload link.
https://github.com/imagerelay/api/blob/master/sections/upload_links.md

Get Folder Links
---------------

* `GET folder_links.json` will return a list of folder links associated with your account.

We will return 100 files per page. If the result set has more than 100 folder links, it's your responsibility to check the next page to see if there are any more folder links -- you do this by adding `&page=2` to the query, then `&page=3` and so on.

```json
[
  {
    "id": "<folder_link_id>",
    "uid": "93527abc0258448885d5b388f70cd654",
    "user_id": "<user_id>",
    "purpose": "testing api creation",
    "expires_on": null,
    "allows_download": true,
    "view_count": 0,
    "created_at": "2015-06-04T20:06:07Z",
    "updated_at": "2015-06-04T20:06:07Z",
    "show_tracking": true,
    "folder_link_url": "http://yoururl.imagerelay.com:3000/fl/93527abc0258448885d5b388f70cd654",
    "folder_id": "<folder_id>"
  },
  {
    "id": "<folder_link_id>",
    "uid": "b9d1a51601624f67a055f663c5852f24",
    "user_id": "<user_id>",
    "purpose": "testing api creation",
    "expires_on": "2015-07-01T00:00:00Z",
    "allows_download": true,
    "view_count": 0,
    "created_at": "2015-06-04T20:05:27Z",
    "updated_at": "2015-06-04T20:05:27Z",
    "show_tracking": true,
    "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
    "folder_id": "<folder_id>"
  },
]
```

Get Folder Link
---------------

* `GET folder_links/<folder_link_id>.json` will return a folder link.

```json
{
  "id": "<folder_link_id>",
  "uid": "b9d1a51601624f67a055f663c5852f24",
  "user_id": "<user_id>",
  "purpose": "testing api creation",
  "expires_on": "2015-07-01T00:00:00Z",
  "allows_download": true,
  "view_count": 0,
  "created_at": "2015-06-04T20:05:27Z",
  "updated_at": "2015-06-04T20:05:27Z",
  "show_tracking": true,
  "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
  "folder_id": "<folder_id>"
},
```

Create Folder Links
---------------

* `POST folder_links.json` will create a new folder link.

The Content-Type header should be `application/json`. `purpose` is defined by you and can be whatever you like.

If the invite is successful, the call will return `201 CREATED`.
```json
{
  "folder_id":"<folder_id>",
  "allows_download": true,
  "expires_on": "",
  "show_tracking": true,
  "purpose": "testing api"
}
```

We will return a representation of the folder link.

```json
{
  "id": "<folder_link_id>",
  "uid": "b9d1a51601624f67a055f663c5852f24",
  "user_id": "<user_id>",
  "purpose": "testing api creation",
  "expires_on": "2015-07-01T00:00:00Z",
  "allows_download": true,
  "view_count": 0,
  "created_at": "2015-06-04T20:05:27Z",
  "updated_at": "2015-06-04T20:05:27Z",
  "show_tracking": true,
  "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
  "folder_id": "<folder_id>"
},
```

Delete Folder Links
-----------------

* `DELETE folder_links/<folder_link_id>.json` will delete a folder link from your account.

The Content-Type header should be `application/json`

If the delete is successful, the call will return `204 No Content`.
