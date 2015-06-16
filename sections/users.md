Users
===========

Allows you to retrieve users.

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
	    "login": "login",
	    "first_name": "First Name",
	    "last_name": "Last Name",
	    "email": "example@imagerelay.com",
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
```

Get User
---------
* `GET /users/20.json` will return `200 OK` and a representation of the specified user.

```json
{
    "id": 405,
    "login": "login",
    "first_name": "First Name",
    "last_name": "Last Name",
    "email": "example@imagerelay.com",
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