Keywording
============

Keywording allows you to add searchable keywords to your assets.


Keyword Sets
============

Keyword sets are groups of keywords that can be associated with an asset.

Get Keyword Sets
----------------
* `GET /keyword_sets.json` will return `200 OK` and the API user's list of keyword sets.

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more keyword sets -- you do this by adding `&page=2` to the query, then `&page=3` and so on.

```json
[
  {
	"id": "<keyword_set_id1>",
	"name": "Test",
	"created_at": "2015-06-15T11:30:21Z",
	"updated_at": "2015-06-15T11:30:21Z",
	"deleted_at": null
  },
  {
    "id": "<keyword_set_id2>",
    "name": "Test 2",
    "created_at": "2015-06-12T18:21:43Z",
    "updated_at": "2015-06-12T18:22:07Z",
    "deleted_at": null
  },
]
```

Get Keyword Set
---------------
* `GET /keyword_sets/<keyword_set_id>.json` will return `200 OK` and the requested keyword set.

```json
{
    "id": "<keyword_set_id>",
    "name": "Test",
    "created_at": "2015-06-15T11:30:21Z",
    "updated_at": "2015-06-15T11:30:21Z",
	"deleted_at": null
}
```

Create Keyword Set
------------------
* `POST /keyword_sets.json` will create a new keyword set.

```json
{
	"name":"Sample API Keyword Set"
}
```

We will return `201 CREATED` and a representation of the new keyword set. Once a keyword set is created, it will be initially empty. Then, individual keywords can be created and added to the keyword set. See below.


```json
{
  "id": "<new_keyword_set_id>",
  "name": "Sample API Keyword Set",
  "created_at": "2015-06-16T08:52:12Z",
  "updated_at": "2015-06-16T08:52:12Z",
  "deleted_at": null
}
```

Update Keyword Set
------------------
* `PUT /keyword_sets/<keyword_set_id>.json` will update the `name` of a keyword set.
```json
{
	"name":"New Keyword Set Name"
}
```
Will return `200 OK` and a representation of the keyword set.

```json
{
  "id": "<keyword_set_id>",
  "name": "New Keyword Set Name",
  "created_at": "2015-06-16T08:52:12Z",
  "updated_at": "2015-06-16T08:52:12Z",
  "deleted_at": null
}
```

Delete Keyword Set
-------------------
* `DELETE /keyword_sets/<keyword_set_id>.json` will delete a keyword set and return `204 NO-CONTENT`. All associated keywords will also be deleted.
_Note: If identical keywords exists in multiple keyword sets, only the keyword in the deleted set will be deleted._

Keywords
========

Keywords are associated with keyword sets and are the searchable asset terms.

Get Keywords
------------
* `GET /keyword_sets/<keyword_set_id>/keywords.json` will return `200 OK` and a list of keywords associated with the specified keyword set.

```json
[
  {
    "id": "<keyword_id1>",
    "keyword_set_id": "<keyword_set_id>",
    "name": "Color",
    "created_at": "2015-06-15T12:34:36Z",
    "updated_at": "2015-06-15T14:05:34Z"
  },
  {
    "id": "<keyword_id2>",
    "keyword_set_id": "<keyword_set_id>",
    "name": "Size",
    "created_at": "2015-06-16T08:59:48Z",
    "updated_at": "2015-06-16T08:59:48Z"
  },
]
```

Get Keyword
-----------
* `GET /keyword_sets/<keyword_set_id>/keywords/<keyword_id>.json` will return `200 OK` and a representation of the keyword requested.

```json
{
	"id": "<keyword_id>",
	"keyword_set_id": "<keyword_set_id>",
	"name": "Color",
	"created_at": "2015-06-15T12:34:36Z",
	"updated_at": "2015-06-15T14:05:34Z"
}
```

Create Keyword
--------------
* `POST /keyword_sets/<keyword_set_id>/keywords.json` will create a new keyword and associate it with the specified keyword set.

```json
{
	"name":"New Keyword"
}
```

We will return `201 CREATED` and a representation of the new keyword

```json
{
  "id": "<keyword_id>",
  "keyword_set_id": "<keyword_set_id>",
  "name": "New Keyword",
  "created_at": "2015-06-16T09:07:30Z",
  "updated_at": "2015-06-16T09:07:30Z"
}
```

Update Keyword
--------------
* `PUT /keyword_sets/"<keyword_set_id>"/keywords/"<keyword_id>".json` will update a keyword.

```json
{
	"name":"Updated Keyword"
}
```

We will return `200 OK` and a representation of the updated keyword.

```json
{
  "id": "<keyword_id>",
  "keyword_set_id": "<keyword_set_id>",
  "name": "Updated Keyword",
  "created_at": "2015-06-16T09:07:30Z",
  "updated_at": "2015-06-16T09:07:30Z"
}
```

Delete Keyword
--------------
* `DELETE /keyword_sets/<keyword_set_id>/keywords/<keyword_id>.json` will delete a keyword and return `204 NO-CONTENT`.
