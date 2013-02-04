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

To test things out and get started, you can use http basic authenitication with the IR API. In production, you should use the supported oauth2 authentication. That way you don't have to worry about
storing Image Relay usernames' and passwords' in your own application. Click [here] (#) for more detailed information regarding
Image Relay oauth authentication.


Identify your app
-----------------

You must include a `User-Agent` header with the name of your application and a link to it or your email address so 
we can get in touch in case you're doing something wrongor something great. Here's an example:

    User-Agent: Freshbooks (http://freshbooks.com)

If you don't supply this header, you will get a `400 Bad Request`.

Thanks
------

These API documents have been modeled closely after those provided by [37signals] (http://37signals.com) for their [API] (https://github.com/37signals/bcx-api/blob/master/README.md). A big thank you to them for doing what they do.

