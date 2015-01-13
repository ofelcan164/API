The Image Relay API
===================

The Image Relay API allows IR users to access many Image Relay features through a JSON RESTful web interface.

Making a Request
----------------

All requests start with https://[company url].imagerelay.com/api/v2/

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
  https://api.imagerelay.com/api/v2/folders/555/children.json
```
Authentication
--------------

To test things out and get started, you can use http basic authentication with the IR API. In production, you should use the supported oauth2 authentication. That way you don't have to worry about storing Image Relay usernames' and passwords' in your own application. Click [here] (https://github.com/imagerelay/API/blob/master/sections/authentication.md) for more detailed information regarding oauth authentication.


Identify your app
-----------------

You must include a `User-Agent` header with the name of your application and a link to it or your email address so 
we can get in touch in case you're doing something wrongor something great. Here's an example:

    User-Agent: Freshbooks (http://freshbooks.com)

If you don't supply this header, you will get a `400 Bad Request`.

Rate limiting
-------------

You can perform up to 500 requests per 10 second period from the same IP address for the same account. If you exceed this limit, you'll get a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response for subsequent requests. Check the `Retry-After` header to see how many seconds to wait before retrying the request.

APIs (this list will be updated as we add more features to our API)
-------------------------------------------------------------------

* [Files] (https://github.com/imagerelay/api/blob/master/sections/files.md)
* [Folders] (https://github.com/imagerelay/api/blob/master/sections/folders.md)
* [Quick Links] (https://github.com/imagerelay/api/blob/master/sections/quick_links.md)
* [File Types] (https://github.com/imagerelay/api/blob/master/sections/file_types.md)
* [Uploads] (https://github.com/imagerelay/api/blob/master/sections/uploads.md)
* [Users] (https://github.com/imagerelay/api/blob/master/sections/users.md)

Thanks
------

These API documents have been modeled closely after those provided by [37signals] (http://37signals.com) for their [API] (https://github.com/37signals/bcx-api/blob/master/README.md).

Errors
------
If you find a typo or an error in the documentation, we welcome pull requests.

