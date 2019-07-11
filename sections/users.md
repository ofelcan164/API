Users
===========

Allows you to retrieve users.

Get Yourself (authenticated user)
----------

* `GET /users/me.json` will return `200 OK` information relating to the currently authenticated user.

```json
{
  "id": 42,
  "login": "your-login",
  "email": "email@company.com",
  "company": "Company Name",
  "first_name": "FirstName",
  "last_name": "LastName",
  "permission_group_id": 1234,
  "permissions": [
    {
      "name": "Permission One",
      "description": "Description of permissions associated",
      "id": 1
    },
    {...}
  ]
}
```

Get Users
----------
* `GET /users.json` will return `200 OK` and a list of users belonging to your account, 100 users per page (`?page=X`).

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

Get a user's Quick Links
---------
* `GET /users/42/quick_links.json` will return `200 OK` with a list of quick links the user created, 100 per page (`?page=X`).

```json
[
  {
    "id": 12345,
    "uid": "GUID",
    "purpose": "purpose of the quick link",
    "created_at": "2008-01-1T00:00:00.000Z",
    "processing": false,
    "asset_id": 2187,
    "user_id": 42,
    "filename": "filename.jpg",
    "url": "https://your-company.imagerelay.com/share/GUID"
  },
  {...}
]
```