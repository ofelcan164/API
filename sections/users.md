Users
===========

Allows you to retrieve users.

Get Yourself (authenticated user)
----------

* `GET /users/me.json` will return `200 OK` information relating to the currently authenticated user.

```json
{
  "id": "<user_id>",
  "login": "your-login",
  "email": "email@company.com",
  "company": "Company Name",
  "first_name": "FirstName",
  "last_name": "LastName",
  "permission_group_id": "<permission_group_id>",
  "permissions": [
    {
      "name": "Permission One",
      "description": "Description of permissions associated",
      "id": "<permission_group_id>"
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
	    "id": "user_id1>",
	    "login": "mldorm",
	    "first_name": "Michael",
	    "last_name": "Dorm",
	    "email": "michael@dorm.com",
	    "company": "",
	    "created_on": null,
	    "updated_on": "2008-04-22T11:54:57Z",
	    "permission_id": "permission_group_id>",
	    "custom_field_one": null,
	    "custom_field_two": null,
	    "custom_field_three": null,
	    "custom_field_four": null
	},
	{
	    "id": "user_id2>",
	    "login": "login",
	    "first_name": "First Name",
	    "last_name": "Last Name",
	    "email": "example@imagerelay.com",
	    "company": "IR",
	    "created_on": "2008-03-24T21:19:14Z",
	    "updated_on": "2015-05-22T14:30:34Z",
	    "permission_id": "<permission_group_id>",
	    "custom_field_one": null,
	    "custom_field_two": null,
	    "custom_field_three": null,
	    "custom_field_four": null
	}
]
```

Search Users
----------
* `GET /search.json?<query_param>=Dorm` will return `200 OK` and a list of users belonging to your account that match the search term ("Dorm" in this example), 100 users per page (`?page=X`). Searches are performed against the fields `first_name`, `last_name`, and `email` which replace `<query_param>` above.

```json
[
	{
	    "id": "<user_id>",
	    "login": "mldorm",
	    "first_name": "Michael",
	    "last_name": "Dorm",
	    "email": "michael@dorm.com",
	    "company": "",
	    "created_on": null,
	    "updated_on": "2008-04-22T11:54:57Z",
	    "permission_id": "<permission_group_id>",
	    "custom_field_one": null,
	    "custom_field_two": null,
	    "custom_field_three": null,
	    "custom_field_four": null
	}
]
```

Get User
---------
* `GET /users/<user_id>.json` will return `200 OK` and a representation of the specified user.

```json
{
    "id": "<user_id>",
    "login": "login",
    "first_name": "First Name",
    "last_name": "Last Name",
    "email": "example@imagerelay.com",
    "company": "IR",
    "created_on": "2008-03-24T21:19:14Z",
    "updated_on": "2015-05-22T14:30:34Z",
    "permission_id": "<permission_group_id>",
    "custom_field_one": null,
    "custom_field_two": null,
    "custom_field_three": null,
    "custom_field_four": null
},
```

Get a user's Quick Links
---------
* `GET /users/<user_id>/quick_links.json` will return `200 OK` with a list of quick links the user created, 100 per page (`?page=X`).

```json
[
  {
    "id": "<quick_link_id>",
    "uid": "GUID",
    "purpose": "purpose of the quick link",
    "created_at": "2008-01-1T00:00:00.000Z",
    "processing": false,
    "asset_id": "<asset_id>",
    "user_id": "<user_id>",
    "filename": "filename.jpg",
    "url": "<quick_link_url>"
  },
  {...}
]
```

Create SSO User (if you have SSO setup)
--------------

* `POST /users/sso_user.json` will create a new SSO user.

For SSO-enabled accounts, you may want to create SSO users in lieu of turning on JIT user creation. Make sure the email address in the JSON matches the user's email in your user database, otherwise they won't be able to login with SSO. The POST body JSON should be the following:

```json
{
  "first_name": "FirstName",
  "last_name": "LastName",
  "email": "name@company.com",
  "company": "Your Company",
  "role_id": "permission_group_id>"
}
```

This will return `201 Created`, if successful.

Update User's Role/Permissions Group
--------------


* `PUT /users/<user_id>.json` will update a user's role.
```json
{
	"role_id": "<permission_group_id>"
}
```

Will return a `200 OK` response and a JSON representation of the user.
