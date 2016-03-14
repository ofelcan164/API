Folders
=======

Folders are one of the main ways to keep files organized and findable in Image Relay.

Get Folders
-----------

* `GET /folders.json` will return all top-level folders viewable by the user
* `GET /folders/555/children` will return all the child folders of the specified parent folder.

```json
[
  {
    "asset_count":1,
    "child_count":0,
    "created_on":"2012-06-19T08:41:19Z",
    "id":11136,"metagroup_id":null,
    "name":"McCadam Logos",
    "parent_id":6527,"
    updated_on":"2012-07-23T15:39:16Z",
    "user_id":405
  },
  {
    "asset_count":47,
    "child_count":1,"
    created_on":"2012-10-09T12:09:25Z",
    "id":11150,
    "metagroup_id":null,
    "name":"Product Photography",
    "parent_id":6527,
    "updated_on":"2012-10-09T12:09:25Z",
    "user_id":405
  }
]
```

Get Root Folder

* `GET /folders/root.json` will return the root of all the folders for this user. This folder isn't visible in the UI, calling children on this folder is the equivalent of
calling `GET /folders.json`

```json
{
  "created_on":"2008-06-23T20:29:10Z",
  "id":6527,
  "metagroup_id":null,
  "name":"0",
  "parent_id":null,
  "updated_on":"2012-04-11T15:23:32Z",
  "user_id":0
}
```

Get Folder
----------

* `GET /folders/555.json` will return the specified folder.

```json
{
  "created_on":"2012-06-19T08:41:19Z",
  "id":11136,"metagroup_id":null,
  "name":"McCadam Logos",
  "parent_id":6527,
  "updated_on":"2012-07-23T15:39:16Z",
  "user_id":405
}
```

Create Folder
-------------

* `POST /folders/555/children` will create a new folder that is a child of the specified parent folder.

```json
{
  "name": "My New Folder Name"
}
```

This will return `201 Created`, if successful.

Update Folder
-------------

* `PUT /folders/555.json` will update the folder from the parameters passed in.

```json
{
  "name": "A new Name for the folder"
}
```

This will return `200 OK` if the update was successful, along with a JSON representation of the folder.

Delete Folder
-------------

* `DELETE /folders/555.json` will delete the folder with the id passed in the URL.

This will return `204 No Content` if successful.


