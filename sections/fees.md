# Fees

Bidsketch users can save fees to their account to be reused in future proposals.

## Get Fees

* `GET /fees.json` will list all the fees saved to the account

```json
[
  {
    "id": 187375,
    "name": "Repairs",
    "url": "http://bidsketch.com/api/v1/fees/187375.json",
    "app_url": "http://hvactothefuture.bidsketch.com/fees/187375",
    "created_at": "2015-01-05T15:31:42-05:00",
    "updated_at": "2015-01-05T15:31:42-05:00",
    "category": "HVAC Repair",
    "total": 1615.0,
    "feetype": "hourly",
    "details": "$1,615 (19 hours @ $85/hour)"
  },
  {
    "id": 187371,
    "name": "Time Travel",
    "url": "http://bidsketch.com/api/v1/fees/187371.json",
    "app_url": "http://hvactothefuture.bidsketch.com/fees/187371",
    "created_at": "2015-01-05T13:02:00-05:00",
    "updated_at": "2015-01-05T13:41:32-05:00",
    "category": "HVAC Repair",
    "total": 1210.0,
    "feetype": "fixed",
    "details": "$1,210"
  }
]
```

## Get Fee

* `GET /fees/1.json` to get a single fee

```json
{
  "id": 187375,
  "name": "Repairs",
  "url": "http://bidsketch.com/api/v1/fees/187375.json",
  "app_url": "http://hvactothefuture.bidsketch.com/fees/187375",
  "created_at": "2015-01-05T15:31:42-05:00",
  "updated_at": "2015-01-05T15:31:42-05:00",
  "category": "HVAC Repair",
  "quantity": 19,
  "total": 1615.0,
  "currency": "USD",
  "amount": 85.0,
  "unit": "Hour",
  "details": "$1,615 (19 hours @ $85/hour)",
  "feetype": "hourly",
  "description": "<p>For Mayor Wilson's Office, we estimate 19 hours of total work, across all timelines. This includes parts and materials.</p>"
}
```

## Create Fee

* `POST /fees.json` will create a fee with the provided data

```json
{
  "name": "Labor",
  "feetype": "hourly",
  "amount": 50,
  "quantity": 4,
  "description": "<p>We are not working for free.</p>"
}
```

## Update Fee

* `PUT /fees/1.json` will update a fee with the provided data

```json
{
  "feetype": "custom",
  "amount": 8000,
  "quantity": 4,
  "unit": "Plutonium Stick"
}
```

### Delete Fee

* `DELETE /fees/1.json` will delete that fee
