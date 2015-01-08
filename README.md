How to Make Friends and Use the Bidsketch API
=============

## Making a request

Your adventure with the Bidsketch API starts at `https://bidsketch.com/api/v1`. This is the beginning of every end point. 

```
curl https://bidsketch.com/api/v1/proposals -H 'Authorization: Token token="yourtoken"'
```

## Authentication

We use HTTP token authentication to identify and authorize accounts for the API. All you need to do as a developer is ask our users to get their api token and pass it along in an authorization header.

```
Authorization: Token token="abc123abc123abc123abc123abc123"
```

Users can find their api tokens at `[subdomain].bidsketch.com/account/api_tokens`. Keep in mind that **only Admin users can manage api tokens**.

## Versioning

We're starting this api with a nice, comfortable version 1, hence the `v1/` part of the api path. This just means that you can trust that `v1` will keep working the way you expect it. When we have to introduce something that could break what you have worked so hard to build, we'll bump the version of the API up one.

## Rate Limits

We limit requests for each token to **100 requests in 20 seconds**.

## Status Codes

| Code | Reason | When You'll See It |
| ----:| ------ | ------------------ |
| 200  | OK. Cool. | Successful `GET`, `PUT`, and `POST` requests |
| 204  | No Content | Successful `DELETE` requests |
| 400  | Bad Request | No API token was provided |
| 401  | Unauthorized | Revoked or Invalid API token |
| 404  | Not Found | Can't find the API resource you asked for |
| 422  | Unprocessible Entity | Invalid data when creating or updating |
| 426  | Upgrade Required | The account has hit a client or proposal limit |

### Errors

Whenever you get a **`422 Unprocessible Entity`** code, it'll have a json-formatted array of errors for what went wrong:

```json
{
  "errors": [
    "email cannot be blank",
    "first_name is far too silly",
    "last_name matches first_name. Who has two first names?"
  ]
}
```

