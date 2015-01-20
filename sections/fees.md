# Fees

Bidsketch users can save fees to their account to be reused in future proposals.

## Fee Data

* Required attributes are **bold**.  
* Attributes required under certain conditions are _italic_.
* Attributes that can be set using `create` and `update` are marked with an asterisk(*)

Attribute | Type | Info | Example
--------- | ---- | ---- | -------
**`name*`** | string | The name of a fee | `Repairs`
**`amount*`** | float | The amount of a fee. For fixed fees, this is a total. For calculated fees, this is the amount per unit. | `85.0`
**`feetype*`** | string | Specifies the type of fee. **Must be one of `fixed`, `hourly`, `monthly`, `yearly`, or `custom`** | `hourly`, `monthly`, `yearly`, `fixed`, or `custom`
_`unit*`_ | string | The unit used when labeling custom fees. Only settable with `custom` fees. Will be `Hour` for `hourly`, `Month` for `monthly`, and `Year` for `yearly`. | `Hour`
`quantity*` | integer | The quantity used for calculated fees. | `19`
`category*` | string | A fee category to group fees together. Can be any string. | `HVAC Repair`
`description*`| html | HTML formatted content | `<p>For Mayor Wilson's Office, we estimate 19 hours of total work, across all timelines. This includes parts and materials.</p>`
`id` | integer | The unique id for a fee | `187375`
`url` | string | The API url for the fee | `http://bidsketch.com/api/v1/fees/187375.json`
`app_url` | string | The Bidsketch app url for the fee | `http://hvactothefuture.bidsketch.com/fees/187375`
`created_at` | datetime | When the fee was created | `2015-01-05T15:31:42-05:00`
`updated_at` | datetime | when the fee was last updated | `2015-01-05T15:31:42-05:00`
`total` | float | The total amount of the fee. If the fee is calculated this will be the `amount` multiplied by the `quantity` | `1615.0`
`currency` | string | An [ISO currency code](http://en.wikipedia.org/wiki/ISO_4217) that represents the proposal currency | `USD`
`details` | string | A formatted label for the fee | `$1,615 (19 hours @ $85/hour)`

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
