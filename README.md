# Auth0 + Shiny Server middleware

## Tan's notes

auth0 x express.js proxy middleware that helps achieve an auth0-walled shiny server open source instance. 

originally found via Charles Bordet, [notes](https://www.charlesbordet.com/en/guide-shiny-aws/#use-auth0-as-an-authentication-server) may also be helpful if stuck

## Running the proxy
In order to run this proxy you need to have npm and nodejs installed.

You also need to set the ClientSecret, ClientId and Domain for your Auth0 app as environment variables with the following names respectively: `AUTH0_CLIENT_SECRET`, `AUTH0_CLIENT_ID` and `AUTH0_DOMAIN`.

For that, if you just create a file named `.env` in the directory and set the values like the following, the app will just work:

````bash
# .env file
AUTH0_CLIENT_SECRET=myCoolSecret
AUTH0_CLIENT_ID=myCoolClientId
AUTH0_DOMAIN=myCoolDomain
AUTH0_CALLBACK_URL=https://my.url.com/
COOKIE_SECRET=somethingRandomHerePlease
SHINY_HOST=localhost
SHINY_PORT=3838
PORT=3000
LOGOUT_URL=https://my.url.com/afterLogout
````

Once you've set those 3 environment variables, just run `npm start` and try calling [http://localhost:3000/](http://localhost:3000/)


For further customization you can add the following variables to your `.env` file

```bash
# Auto login if the session exists on Auth0 Server
CHECK_SESSION=true
# When logout is called, log the user out of Auth0 aswell
LOGOUT_AUTH0=true
# When logging out is called, must logout of remote idp aswell
# This will force LOGOUT_AUTH0 to true
LOGOUT_FEDERATED=true
```
