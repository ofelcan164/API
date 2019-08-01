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

1. Register your application with Image Relay. You need an Image Relay account to do this. Once logged in to IR, click on "My Account" in the upper right corner. Select "Developers" from the menu on the left. You'll need to provide your application name and a callback URI. Please note - you need a __paid__ Image Relay account to do this.

 - The callback URI specified in the configuration must point to a web service or something that is capable of receiving a web request. The request will contain a code that you will use to exchange for an authorization token. https://webhook.site/ is a nice alternative if you are setting this up for the first time.

2. To begin the process of obtaining an OAuth token, visit the authorization endpoint in a web browser - https://launch.imagerelay.com/oauth/authorize...... Below is an example of the full constructed URL.

        https://launch.imagerelay.com/oauth/authorize?response_type=code&client_id=<YOUR_CLIENT_ID>&redirect_uri=https://<YOUR_REDIRECT_URI>&state=<RANDOM_STRING>

3. Upon visiting that URL you will need to login. Once you are logged in, Click the 'Yes give them access button' to grant access and then you will be redirected to the redirect uri that you specified when configuring the application (it should match the redirect_uri param in the url from step 2)

4. Your web service will have received a request with a `code` parameter and value. 

5. Now use the code that your web service received in step 4 to obtain an access token. You can use CURL to perform this request or some other API testing tool of your choosing.

        POST https://launch.imagerelay.com/oauth/token?client_id=<YOUR_CLIENT_ID>&redirect_uri=<YOUR_REDIRECT_URI>&client_secret=<YOUR_CLIENT_SECRET>&code=<AUTH_CODE_FROM_STEP_4>&grant_type=authorization_code

6. Your app can now use the access token you got back from the `POST` request in step 5 to make authorized requests to the Image Relay API. You use the access token in the request by setting the Authorization request header:

        Authorization: OAuth THE_ACCESS_TOKEN

7. Once you get an access token, try it out, you can make a request to get information about the user that just authorized you, by making an authenticated request to 

		GET https://api.imagerelay.com/api/v2/users/me.json


End Points
----------

* `GET https://launch.imagerelay.com/oauth/authorization`
* `POST https://launch.imagerelay.com/oauth/token`

Implementations
---------------
If you are developing your app using ruby, Image Relay has released an omniauth strategy for the IR API. You can find it here: https://github.com/imagerelay/omniauth-imagerelay

We know OAuth2 can be a bit tricky when you are getting started, if you have questions, please e-mail support@imagerelay.com; include your IR URL in your request.
