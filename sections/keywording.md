Keywording
============

Keywording allows you to add searchable keywords to your assets.


Keyword Sets
============

Keyword sets are groups of keywords that can be associated with an asset.

Get Keyword Sets
----------------
* `GET /keyword_sets.json` will return `200 OK` and the API user's list of keyword sets.

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more keyword sets -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
  {
	"id": 18,
	"name": "Test",
	"created_at": "2015-06-15T11:30:21Z",
	"updated_at": "2015-06-15T11:30:21Z",
	"deleted_at": null
  },
  {
    "id": 17,
    "name": "Test 2",
    "created_at": "2015-06-12T18:21:43Z",
    "updated_at": "2015-06-12T18:22:07Z",
    "deleted_at": null
  },
]
```

Get Keyword Set
---------------
* `GET /keyword_sets/555.json` will return `200 OK` and the requested keyword set where 555 represents the id of the keyword set requested.

```json
{
    "id": 555,
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

We will return `201 CREATED` and a representation of the new keyword set.


```json
{
  "id": 19,
  "name": "Sample API Keyword Set",
  "created_at": "2015-06-16T08:52:12Z",
  "updated_at": "2015-06-16T08:52:12Z",
  "deleted_at": null
}
```

Update Keyword Set
------------------
* `PUT /keyword_sets/19.json` will update a keyword set.
```json
{
	"name":"New Keyword Set Name"
}
```
Will return `200 OK` and a representation of the keyword set.

```json
{
  "id": 19,
  "name": "New Keyword Set Name",
  "created_at": "2015-06-16T08:52:12Z",
  "updated_at": "2015-06-16T08:52:12Z",
  "deleted_at": null
}
```

Delete Keyword Set
-------------------
* `DELETE /keyword_sets/19.json` will delete a keyword set and return `204 NO-CONTENT`.

Keywords
========

Keywords are associated with keyword sets and are the searchable asset terms.

Get Keywords
------------
* `GET /keyword_sets/18/keywords.json` will return `200 OK` and a list of keywords associated with a keyword set.

```json
[
  {
    "id": 72,
    "keyword_set_id": 18,
    "name": "Color",
    "created_at": "2015-06-15T12:34:36Z",
    "updated_at": "2015-06-15T14:05:34Z"
  },
  {
    "id": 75,
    "keyword_set_id": 18,
    "name": "Size",
    "created_at": "2015-06-16T08:59:48Z",
    "updated_at": "2015-06-16T08:59:48Z"
  },
]
```

Get Keyword
-----------
* `GET /keyword_sets/18/keywords/72.json` will return `200 OK` and a representation of the keyword requested.

```json
{
	"id": 72,
	"keyword_set_id": 18,
	"name": "Color",
	"created_at": "2015-06-15T12:34:36Z",
	"updated_at": "2015-06-15T14:05:34Z"
}
```

Create Keyword
--------------
* `POST /keyword_sets/18/keywords.json` will create a new keyword and associate it with a keyword set.  The number `18` in the request represents the ID of the keyword set you want to add the keyword to.

```json
{
	"name":"New Keyword"
}
```

We will return `201 CREATED` and a representation of the new keyword

```json
{
  "id": 77,
  "keyword_set_id": 18,
  "name": "New Keyword",
  "created_at": "2015-06-16T09:07:30Z",
  "updated_at": "2015-06-16T09:07:30Z"
}
```

Update Keyword
--------------
* `PUT /keyword_sets/18/keywords/77.json` will update a keyword where `18` represents the ID of the keyword set and `77` represents the ID of the keyword to be updated.
```json
{
	"name":"Updated Keyword"
}
```
We will return `200 OK` and a representation of the updated keyword.
```json
{
  "id": 77,
  "keyword_set_id": 18,
  "name": "Updated Keyword",
  "created_at": "2015-06-16T09:07:30Z",
  "updated_at": "2015-06-16T09:07:30Z"
}
```

Delete Keyword
--------------
* `DELETE /keyword_sets/19/keywords/77.json` will delete a keyword and return `204 NO-CONTENT`.
