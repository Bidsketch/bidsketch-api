How to Make Friends and Use the Bidsketch API
=============

## Making a request

Your adventure with the Bidsketch API starts at `https://bidsketch.com/api/v1`. This is the beginning of every end point. 

```
curl https://bidsketch.com/api/v1/proposals -H 'Authorization: Token token="yourtoken"'
```

## Authentication

`http://imeric.bidsketch.com/account/api_tokens`

## Versioning

## Rate Limits

## Errors

400 Bad Request
```json
{
  "errors": [
    "email cannot be blank",
    "first_name is far too silly",
    "last_name matches first_name. Who has two first names?"
  ]
}

```

## Status Codes

200
201
204
400
401
404
422
426

## Suggestions & Support
