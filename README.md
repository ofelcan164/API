The Image Relay API
===================

The Image Relay API allows IR users to access many Image Relay features through an RESTful web interface.

Making a Request
----------------

All requests start with https://api.imagerelay.com/api/v2/

In curl a request would look like this:

```shell
curl -u user:pass -H 'User-Agent: MyApp (yourname@example.com)' https://api.imagerelay.com/api/v2/folders.json
```
If you are sending data to the API, include the Content-Type header and the data as JSON.

```shell
curl -u username:password \
  -H 'Content-Type: application/json' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  -d '{ "name": "New Catalog" }' \
  https://api.imagerelay.com/api/v2/folders/555/new_child.json
```
Authentication
--------------
