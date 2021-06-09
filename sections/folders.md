Folders
=======

Folders are one of the main ways to keep files organized and findable in Image Relay.

Get Folders
-----------

* `GET /folders.json` will return all top-level folders viewable by the user
* `GET /folders/<parent_folder_id>/children` will return all the child folders of the specified parent folder.

```json
[
  {
    "asset_count":1,
    "child_count":0,
    "created_on":"2012-06-19T08:41:19Z",
    "id":"<folder_id>",
    "metagroup_id":null,
    "name":"McCadam Logos",
    "parent_id":"<parent_folder_id>",
    "updated_on":"2012-07-23T15:39:16Z",
    "user_id":"<user_id>"
  },
  {
    "asset_count":47,
    "child_count":1,"
    created_on":"2012-10-09T12:09:25Z",
    "id":"<folder_id>",
    "metagroup_id":null,
    "name":"Product Photography",
    "parent_id":"<parent_folder_id>",
    "updated_on":"2012-10-09T12:09:25Z",
    "user_id":"<user_id>"
  }
]
```

Get a folder's children, paginated, 100 per page

 * `GET /folders/<folder_id>/children?page=1` will return a paginated set of children folders along with pagination information.

 **Please note the unpaginated version of this endpoint will be deprecated in the near future so please use this version if building a new integration**

```json
{
    "folders": [
      {
        "asset_count":1,
        "child_count":0,
        "created_on":"2012-06-19T08:41:19Z",
        "id":"<folder_id>",
        "metagroup_id":null,
        "name":"McCadam Logos",
        "parent_id":6527,"
        updated_on":"2012-07-23T15:39:16Z",
        "user_id":"<user_id>"
      },
      {
        "asset_count":47,
        "child_count":1,"
        created_on":"2012-10-09T12:09:25Z",
        "id":"<folder_id>",
        "metagroup_id":null,
        "name":"Product Photography",
        "parent_id":6527,
        "updated_on":"2012-10-09T12:09:25Z",
        "user_id":"<user_id>"
      }
    ],
    "pagination": {
        "current": 1,
        "previous": null,
        "next": 2,
        "per_page": 100,
        "pages": 2,
        "count": 155,
        "prev_page_path": null,
        "next_page_path": "/api/v2/folders/555/children?page=2"
    }
}
```

Get Folder
----------

* `GET /folders/<folder_id>.json` will return the specified folder.

```json
{
  "id":"<folder_id>",
  "metagroup_id":null,
  "name":"McCadam Logos",
  "parent_id":6527,
  "user_id":"<user_id>",
  "created_on":"2012-06-19T08:41:19Z",
  "updated_on":"2012-07-23T15:39:16Z",
}
```

Get Folder Files
----------------
* `GET /folders/<folder_id>/files.json` returns all the files in the specified folder.
For more information regarding files within folders, see [Files](https://github.com/imagerelay/api/blob/master/sections/files.md).
```json
[
  {
    "id":"<file_id>",
    "filename":"basic_perm_icon.png",
    "created_at":"2013-05-20T12:58:07Z",
    "updated_on":"2013-05-20T13:03:36Z",
    "size":7358,
    "width":101,
    "height":101,
    "content_type":"image/png",
    "user_id":"<user_id>",
    "deleted":null,
    "deletion_date":null,
    "delete_user_id":null,
    "file_type_id":"<file_type_id>",
    "terms":
      [
        {
          "term_id":"<term_id1>",
          "value":" "
        },
        {
          "term_id":"<term_id2>",
          "value":" "
        },
        {
          "term_id":"<term_id3>",
          "value":" "
        },
        {
          "term_id":"<term_id4>",
          "value":" "
        }
      ],
      "tags":
      [
        {
          "tag_id":"<tag_id1>",
          "value":"Sports"
        },
        {
          "tag_id":"<tag_id2>",
          "value":"Marketing"
        }
      ]
  },
  {
    "id": "<file_id>",
    "filename":"grey_lock_icon.png",
    "created_at":"2013-05-20T12:58:05Z",
    "updated_on":"2013-05-20T13:03:33Z",
    "size":2974,
    "width":15,
    "height":19,
    "content_type":"image/png",
    "user_id":"<user_id>",
    "deleted":null,
    "deletion_date":null,
    "delete_user_id":null,
    "file_type_id":"<file_type_id>",
    "terms":
      [
        {
          "term_id":"<term_id1>",
          "value":" "
        },
        {
          "term_id":"<term_id2>",
          "value":" "
        },
        {
          "term_id":"<term_id3>",
          "value":" "
        },
        {
          "term_id":"<term_id4>",
          "value":" "
        }
      ],
    "tags":
      [
        {
          "tag_id":"<tag_id1>",
          "value":"Sports"
        },
        {
          "tag_id":"<tag_id2>",
          "value":"Marketing"
        }
      ]
  }
]
```

Get Root Folder
---------------

* `GET /folders/root.json` will return the root of all the folders for this user. This folder isn't visible in the UI, calling children on this folder is the equivalent of
calling `GET /folders.json`.

```json
{
  "root_id":"<root_folder_id>"
}
```
_Note: This is mainly for top-level folder manipulation._

Create Folder
-------------

* `POST /folders/<root_folder_id>/children` will create a new top-level folder.

```json
{
  "name": "My New Folder Name"
}
```

* `POST /folders/<parent_folder_id>/children` will create a new folder that is a child of the specified parent folder.

```json
{
  "name": "My New Folder Name"
}
```


This will return `201 Created` and a JSON representation of the file created, if successful.

```json
{
    "id": "<new_folder_id>",
    "name": "New folder name",
    "user_id": "<user_id>",
    "created_on": "2021-06-09T15:46:55.000Z",
    "updated_on": "2021-06-09T15:46:55.000Z",
    "parent_id": "<root_folder_id>/<parent_folder_id>",
    "metagroup_id": null,
    "folder_asset_id": null,
    "folder_image_x": null,
    "folder_image_y": null,
    "folder_image_z": null,
    "all_names": null,
    "all_ids": null,
    "external_id": null,
    "deleted_timestamp": 0
}
```

Update Folder
-------------

* `PUT /folders/<folder_id>.json` will update the folder name from the parameter `name` passed in.

```json
{
  "name": "A new Name for the folder"
}
```

This will return `200 OK` if the update was successful, along with a JSON representation of the folder.

Delete Folder
-------------

* `DELETE /folders/<folder_id>.json` will delete the specified folder.

This will return `204 No Content` if successful.
