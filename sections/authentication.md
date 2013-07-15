Image Relay API Authentication
==============================

Image Relay uses the OAuth2 protocol to authorize requests to the Image Relay API. We conform to the [draft-10](http://tools.ietf.org/html/draft-ietf-oauth-v2-10) standard.

Basic Auth
----------

To get started with Image Relay's API, you can use HTTP Basic authentication with your own username and password:

```shell
curl -u username:password -H 'User-Agent: MyApp (yourname@example.com)' https://[your_company].imagerelay.com/api/v2/folders.json
```
_You should not be asking other users for usernames and passwords_

You're free to use your own username & password to access your own account and to get started with the API. For deployed applications that require you to authenticate other users, you must use OAuth2 instead of basic authentication.

OAuth 2
-------

1. Register your application with Image Relay. You need an Image Relay account to do this. Once logged in to IR, click on "My Account" in the upper right corner. Select "Developers" from the menu on the left. You'll need to provide your application name and a callback URI.

2. Redirect the user ot our authorization endpoint, https://launch.imagerelay.com/oauth/authorize

        https://launch.imagerelay.com/oauth/authorize?response_type=code&client_id=tl0qsa4bywailemgtcxi7t4aw7ev7pk&redirect_uri=http%3A%2F%2Fdev.lvh.me%3A3001%2Fauth%2Fimagerelay%2Fcallback&state=75eb9a69287f8e2d7836fe1755d719216d02a9a44843dcb7

3. We authenticate the user's Image Relay account, and ask if they want to grant your app access to their account.

4. If the user says ok, we redirect the user back to your app with a verification code.

5. Your app then uses the verification code to request an access token. We authenticate your app with the verification code and send you back an access token.

        POST https://launch.imagerelay.com/oauth/token?client_id=your_client_id&redirect_uri=your_callback_uri&client_secret=your_client_secret&code=code_you_received_in_prior_request

6. Your app can then use the access token you get back from that call to authorize requests to the Image Relay API. You use the access token in the request by setting the Authorization request header:

        Authorization: OAuth THE_ACCESS_TOKEN

Once you get an access token, try it out, you can make a request to get information about the user that just authorized you, by making an authenticated request to `GET https:\\[your company].imagerelay.com\api\v2\users\me.json`


End Points
----------

* `GET https://launch.imagerelay.com/oauth/authorization`
* `GET https://launch.imagerelay.com/oauth/tokens`

Implementations
---------------
If you are developing your app using ruby, Image Relay has released an omniauth strategy for the IR API. You can find it here: https://github.com/imagerelay/omniauth-imagerelay

We know OAuth2 can be a bit tricky when you are getting started, if you have questions, please e-email support@imagerelay.com, please include your IR URL in your request.




