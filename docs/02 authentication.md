# Authentication

The "**PayLata**" API uses a "**Secret Key**" along with a "**Clinet Id**" in order to authenticate a merchant to then generate an "**access token**" which is used to access all other accessible routes within the PayLata platform.

In order to generate an **access token** a **POST** request should be submitted to the "**/auth/token**" route with a **JSON** request body containing the "**client id**" and "**secret key**":

```json
{
    "client_id": "<merchant_client_id>",
    "client_secret": "<merchant_client_secret_key>"
}
```
