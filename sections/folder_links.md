Folder Links
===========

Allows you to retrieve information about, create, or destroy folder links.

Get Folder Links 
---------------

* `GET folder_links.json` will return a list of folder links associated with your account.

We will return 100 files per page. If the result set has more than 100 folder links, it's your responsibility to check the next page to see if there are any more folder links -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
  {
    "id": 53,
    "uid": "93527abc0258448885d5b388f70cd654",
    "user_id": 405,
    "purpose": "testing api creation",
    "expires_on": null,
    "allows_download": true,
    "view_count": 0,
    "created_at": "2015-06-04T20:06:07Z",
    "updated_at": "2015-06-04T20:06:07Z",
    "show_tracking": true,
    "folder_link_url": "http://yoururl.imagerelay.com:3000/fl/93527abc0258448885d5b388f70cd654",
    "folder_id": 12397
  },
  {
    "id": 52,
    "uid": "b9d1a51601624f67a055f663c5852f24",
    "user_id": 405,
    "purpose": "testing api creation",
    "expires_on": "2015-07-01T00:00:00Z",
    "allows_download": true,
    "view_count": 0,
    "created_at": "2015-06-04T20:05:27Z",
    "updated_at": "2015-06-04T20:05:27Z",
    "show_tracking": true,
    "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
    "folder_id": 12397
  },
]
```

Get Folder Link
---------------

* `GET folder_links/555.json` will return a folder link. 555 represents the id of the folder_link you want to return.

```json
{
  "id": 555,
  "uid": "b9d1a51601624f67a055f663c5852f24",
  "user_id": 405,
  "purpose": "testing api creation",
  "expires_on": "2015-07-01T00:00:00Z",
  "allows_download": true,
  "view_count": 0,
  "created_at": "2015-06-04T20:05:27Z",
  "updated_at": "2015-06-04T20:05:27Z",
  "show_tracking": true,
  "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
  "folder_id": 12397
},
```

Create Folder Links
---------------

* `POST folder_links.json` will create a new folder link.

The Content-Type header should be `application/json`

If the invite is successful, the call will return `201 CREATED`. 
```json
{
  "folder_id":"12397",
  "allows_download": true,
  "expires_on": "",
  "show_tracking": true,
  "purpose": "testing api"
}
```

We will return a representation of the folder link.

```json
{
  "id": 52,
  "uid": "b9d1a51601624f67a055f663c5852f24",
  "user_id": 405,
  "purpose": "testing api creation",
  "expires_on": "2015-07-01T00:00:00Z",
  "allows_download": true,
  "view_count": 0,
  "created_at": "2015-06-04T20:05:27Z",
  "updated_at": "2015-06-04T20:05:27Z",
  "show_tracking": true,
  "folder_link_url": "http://yoururl.imagerelay.com/fl/b9d1a51601624f67a055f663c5852f24",
  "folder_id": 12397
},
```

Delete Folder Links
-----------------

* `DELETE folder_links/555.json` will delete a folder link from your account where 555 represents the ID of the folder link.

The Content-Type header should be `application/json`

If the delete is successful, the call will return `204 No Content`.






