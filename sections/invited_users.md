Invited Users
===========

Allows you to retrieve information about users that have been invited to your Image Relay account, invite a new user, or delete a invited user.

Get Invited Users 
---------------

* `GET /invited_users.json` will return a list of invited users to your account.  The invited users will be ordered by the most recently created.

We will return 100 files per page. If the result set has more than 100 invited users, it's your responsibility to check the next page to see if there are any more invited users -- you do this by adding &page=2 to the query, then &page=3 and so on.

```json
[
	{
		"id":99,
		"user_id":405,
		"permission_id":167,
		"first_name":"First Name",
		"last_name":"Last Name",
		"email":"example@imagerelay.com",
		"company":"API Test Company",
		"registration_url": "http://example.imagerelay.com/register/46f9c6866659478a8663953795ea8ce1",
		"created_at":"2015-06-01T20:02:33Z",
		"updated_at":"2015-06-01T20:02:33Z",
		"custom_field_one":null,
		"custom_field_two":null,
		"custom_field_three":null,
		"custom_field_four":null,
		"sub_domain_id":23
	},
	{
		"id":98,
		"user_id":405,
		"permission_id":167,
		"first_name":"First Name",
		"last_name":"Last Name",
		"email":"example@imagerelay.com",
		"company":"API Test Company",
		"registration_url": "http://example.imagerelay.com/register/46f9c6866659478a8663953795ea8ce1",
		"created_at":"2015-06-01T20:02:33Z",
		"updated_at":"2015-06-01T20:02:33Z",
		"custom_field_one":null,
		"custom_field_two":null,
		"custom_field_three":null,
		"custom_field_four":null,
		"sub_domain_id":23
	}
]
```

* `GET /invited_users/97.json` will return the specified invited user.

```json
{
    "id":97,
	"user_id":405,
	"permission_id":167,
	"first_name":"First Name",
	"last_name":"Last Name",
	"email":"example@imagerelay.com",
	"company":"API Test Company",
	"registration_url": "http://example.imagerelay.com/register/46f9c6866659478a8663953795ea8ce1",
	"created_at":"2015-06-01T20:02:33Z",
	"updated_at":"2015-06-01T20:02:33Z",
	"custom_field_one":null,
	"custom_field_two":null,
	"custom_field_three":null,
	"custom_field_four":null,
	"sub_domain_id":23
}
```

Invite New User
---------------

* `POST /invited_users.json` will create a new invited user.

The Content-Type header should be `application/json`

If the invite is successful, the call will return `201 CREATED`.  Otherwise you will receive `400 Bad Request`.

```json
{
	"first_name":"First Name",
	"last_name":"Last Name",
	"email":"example@imagerelay.com",
	"company":"Image Relay",
	"permission_id":"167"
}
```

We will return a response with json data on the new invited user and the user will be sent an invite email to signup for Image Relay.

```json
{
	"id": 100,
	"user_id": 405,
	"permission_id": 167,
	"first_name": "First Name",
	"last_name": "Last Name",
	"email": "example@imagerelay.com",
	"company": "IR",
	"registration_url": "http://example.imagerelay.com/register/46f9c6866659478a8663953795ea8ce1",
	"created_at": "2015-06-02T14:04:07Z",
	"updated_at": "2015-06-02T14:04:07Z",
	"custom_field_one": null,
	"custom_field_two": null,
	"custom_field_three": null,
	"custom_field_four": null,
	"sub_domain_id": 23
}
```

Delete Invited User
--------------------

* `DELETE /invited_users/97.json` will delete a invited user.

This will return `204 No Content`, if successful.








