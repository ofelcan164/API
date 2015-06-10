Invited Users
===========

Allows you to retrieve information about users that have been invited to your Image Relay account, or invite a new user.

Get Invited Users 
---------------

* `GET invited_users` will return a list of invited users to your account.  The invited users will be ordered by the most recently created.

We will return 100 files per page. If the result set has more than 100 invited users, it's your responsibility to check the next page to see if there are any more invited users -- you do this by adding &page=2 to the query, then &page=3 and so on.

Example Response:
```json
{
	"id":99,
	"client_id":23,
	"user_id":405,
	"role_id":167,
	"first_name":"Travis",
	"last_name":"Mathis",
	"email":"travisdmathis@gmail.com",
	"company":"API Test Company",
	"token":"90c1fb538a42414984015aacab8e9d7c",
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

* `POST invited_users` will create a new invited user.

The Content-Type header should be `application/json`

If the invite is successful, the call will return `200 OK`.  Otherwise you will receive `400 Bad Request`.

Required JSON Parameters:
first_name,
last_name,
email,
company,
role_id

We will return a response with json data on the new invited user and the user will be sent an invite email to signup for Image Relay.

Example Response:
```json
{
	"id": 100,
	"user_id": 405,
	"permission_id": 167,
	"first_name": "Travis",
	"last_name": "Mathis",
	"email": "travis@imagerelay.com",
	"company": "IR",
	"token": "46f9c6866659478a8663953795ea8ce1",
	"created_at": "2015-06-02T14:04:07Z",
	"updated_at": "2015-06-02T14:04:07Z",
	"custom_field_one": null,
	"custom_field_two": null,
	"custom_field_three": null,
	"custom_field_four": null,
	"sub_domain_id": 23
}
```




