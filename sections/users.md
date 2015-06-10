Users
===========

Allows you to retrieve information users.

Get Users
----------
* `GET /users` will return `200 OK` and a list of users belonging to your account.

```json
[
	{
	    "id": 1,
	    "login": "mldorm",
	    "first_name": "Michael",
	    "last_name": "Dorm",
	    "email": "michael@dorm.com",
	    "company": "",
	    "created_on": null,
	    "updated_on": "2008-04-22T11:54:57Z",
	    "permission_id": 1,
	    "custom_field_one": null,
	    "custom_field_two": null,
	    "custom_field_three": null,
	    "custom_field_four": null
	},
	{
	    "id": 405,
	    "login": "buffy",
	    "first_name": "Buffy",
	    "last_name": "Miller",
	    "email": "buffy@imagerelay.com",
	    "company": "IR",
	    "created_on": "2008-03-24T21:19:14Z",
	    "updated_on": "2015-05-22T14:30:34Z",
	    "permission_id": 1,
	    "custom_field_one": null,
	    "custom_field_two": null,
	    "custom_field_three": null,
	    "custom_field_four": null
	}
]

Get User
---------
* `GET /users/20.json` will return `200 OK` and a representation of the specified user.

```json
{
    "id": 405,
    "login": "buffy",
    "first_name": "Buffy",
    "last_name": "Miller",
    "email": "buffy@imagerelay.com",
    "company": "IR",
    "created_on": "2008-03-24T21:19:14Z",
    "updated_on": "2015-05-22T14:30:34Z",
    "permission_id": 1,
    "custom_field_one": null,
    "custom_field_two": null,
    "custom_field_three": null,
    "custom_field_four": null
},
```

Get Users Quick Links
---------------

* `GET users/:id/quick_links.json` will return the user's list of quick links where :id is the id of the user whos quick links you want to retrieve.

We will return 100 files per page. If the result set has 100 files, it's your responsibility to check the next page to see if there are any more files -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
{
    "id":437,
    "uid":"999710a0a4f54e248c1ae139ae2199ff",
    "purpose":"api test",
    "created_at":"2015-01-09T20:40:09Z",
    "processing":false,
    "asset_id":242286,
    "user_id":1,
    "filename":"1921996_385805548233952_1402137311_n.jpg",
    "url":"http://your_url.imagerelay.com/share/999710a0a4f54e248c1ae139ae2199ff"}
}
```



