Upload Links
===========

Upload links allow you to quickly share an easy way for someone to upload files to your Image Relay account.

Get Upload Links
---------------

* `GET /upload_links.json` will return `200 OK` the API user's list of upload links

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding `&page=2` to the query, then `&page=3` and so on.

```json
[
    {
        "id": "<upload_link_id>",
        "purpose": "testing upload link",
        "user_id": "<user_id>",
        "uid": "cbd72b7d310744c482847ac4a3d8dcc5",
        "expires_on": null,
        "created_at": "2015-06-05T19:32:10Z",
        "updated_at": "2015-06-05T19:32:10Z",
        "folder_id": "<folder_id>",
        "upload_link_url": "<upload_link_url>"
    },
    {
        "id": "<upload_link_id>",
        "purpose": "testing upload link",
        "user_id": "<user_id>",
        "uid": "c0ef769c9c9f449cb2039202ba61a3de",
        "expires_on": null,
        "created_at": "2015-06-05T19:32:10Z",
        "updated_at": "2015-06-05T19:32:10Z",
        "folder_id": "<folder_id>",
        "upload_link_url": "<upload_link_url>"
    }
]
```

Get Upload Link
--------------

* `GET /upload_links/<upload_link_id>.json` will return `200 OK` and the specified upload link.

```json
{
    "id": "<upload_link_id>",
    "purpose": "testing upload link",
    "user_id": "<user_id>",
    "uid": "c0ef769c9c9f449cb2039202ba61a3de",
    "expires_on": null,
    "created_at": "2015-06-05T19:32:10Z",
    "updated_at": "2015-06-05T19:32:10Z",
    "folder_id": "<folder_id>",
    "upload_link_url": "<upload_link_url>"
}
```

Create Upload Link
-----------------

* `POST /upload_links.json` will create a new upload link for the specified folder. `purpose` is defined by you and can be whatever you like.

```json
{
"purpose":"Testing API",
"folder_id":"12397",
"expires_on":""
}
```

This will return `201 Created`, if successful, as well as a representation of the upload link.

```json
{
  "id": "<upload_link_id>",
  "purpose": "Testing API",
  "user_id": "<user_id>",
  "uid": "fbd601ac0c74487a8d9552f2e4bd04cd",
  "expires_on": null,
  "created_at": "2015-06-09T15:06:33Z",
  "updated_at": "2015-06-09T15:06:33Z",
  "folder_id": "<folder_id>",
  "upload_link_url": "<upload_link_url>"
}
```


Delete Upload Link
-----------------

* `DELETE /upload_links/<upload_link_id>.json` will delete a upload link.

This will return `204 No Content`, if successful.
