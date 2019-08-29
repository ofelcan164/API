Collections
===========

Allows you to retrieve your collections.

Get Collections
----------
* `GET /collections.json` will return `200 OK` and a list of collections the created by the logged in user, 100 collections per page (`?page=X`).

```json
[
	{
    "id": 12345,
    "name": "My Collection",
    "description": null,
    "client_id": 42,
    "user_id": 9,
    "created_on": "2017-11-14T16:02:04.000Z",
    "updated_on": "2019-08-14T13:43:19.000Z",
    "lowres_uid": null,
    "data_export": "",
    "hires_uid": null,
    "deleted_at": null,
    "archived": false,
    "theme_name": "showcase",
    "sorting": "custom",
    "metadata": {
      "public_views": 1
    },
    "modified_at": "2019-08-14T13:42:18.000Z"
	},
	{
    ...
	}
]
```

Get collection
---------
* `GET /collections/12345.json` will return `200 OK` and a representation of the specified collection.

```json
{
  "id": 12345,
  "name": "My Collection",
  "created_on": "2017-11-14T16:02:04.000Z",
  "updated_on": "2019-08-14T13:43:19.000Z",
  "urls": [
    {
      "level": "high_res",
      "description": "High Resolution",
      "url": "https://your-domain.imagerelay.com/sb/high-res-id/my-collection"
    },
    {
      "level": "med_res",
      "description": "Medium Resolution",
      "url": "https://your-domain.imagerelay.com/sb/med-res-id/my-collection"
    },
    {
      "level": "low_res",
      "description": "Low Resolution",
      "url": "https://your-domain.imagerelay.com/sb/low-res-id/my-collection"
    },
    {
      "level": "no_res",
      "description": "View Only",
      "url": "https://your-domain.imagerelay.com/sb/no-res-id/my-collection"
    }
  ]
}
```

Get collection files
---------
* `GET /collections/12345/files.json` will return `200 OK` with a list of files associated with the collection, 100 per page (`?page=X`).

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
    ...
  }
]
```

Create collection
--------------

* `POST /collections.json` will create a new colllection. `name` is required, `asset_ids` is an optional comma separated list of IDs of assets (files) to be added to the new collection.

```json
{
  "name": "New Collection Name",
  "asset_ids": "id1,id2,id3"
}
```

This will return `201 Created`, if successful.

Update collection
--------------

* `PUT /collections/12345.json` will create a new colllection. `name` is required, `asset_ids` is an optional comma separated list of IDs of assets (files) to be added to the new collection.

```json
{
  "name": "New Collection Name",
  "asset_ids": "id1,id2,id3"
}
```

Will return a `200 OK` response and a JSON representation of the user.

Delete collection
--------------

* `DELETE /collections/12345.json` will delete the collection with the given ID.

Will return a `204 No Content` response if the collection was deleted. 
