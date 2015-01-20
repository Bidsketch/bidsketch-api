# Proposal Templates

One of our customers' favorite features is the ability to save proposal templates that can be used as a starting point for new proposals. We're working on overhauling how templates work, so for now the API only exposes the ability to list existing templates and view specific templates.

## Template Data

* Template data is only readable for now
* Nested attributes are indented below their parent with `>`

Attribute | Type | Info | Example
--------- | ---- | ---- | -------
`id` | integer | The unique id for the template | `112683`
`name` | string | A name for the template | `HVAC Repair (Past)`
`created_at` | datetime | When the template was created | `2014-11-05T15:00:40-05:00`
`updated_at` | datetime | When the template was last updated | `2015-01-07T12:12:40-05:00`
`url` | string | The API url for the template | `http://bidsketch.com/api/v1/templates/112683.json`
`app_url` | string | The Bidsketch app url for the template | `http://hvactothefuture.bidsketch.com/proposaltemplates/112683/edit`
`sections[]` | array | A collection of sections associated with the template | An array of section objects
`> url` | string | The API url for the section | `http://bidsketch.com/api/v1/sections/450451.json`
`> id` | integer | The unique id for the section | 450451
`> name` | string | A name for the section | `Frequently Asked Questions`
`> app_url` | string | The Bidsketch app url for the section | `http://hvactothefuture.bidsketch.com/sections/450451`
`> sectiontype` | string | Specifies where the section will appear in a proposal. Must be either `opening` or `closing` | `opening` OR `closing`
`fees[]` | array | A collection of fee associated with the template | An array of fee objects
`> id` | integer | The unique id for a fee | `187375`
`> url` | string | The API url for the fee | `http://bidsketch.com/api/v1/fees/187375.json`
`> app_url` | string | The Bidsketch app url for the fee | `http://hvactothefuture.bidsketch.com/fees/187375`
`> name` | string | The name of a fee | `Repairs`
`> feetype` | string | Specifies the type of fee. **Must be one of `fixed`, `hourly`, `monthly`, `yearly`, or `custom`** | `hourly`, `monthly`, `yearly`, `fixed`, or `custom`

## Get Templates

* `GET /templates.json` will list all the templates saved for the account

```json
[
  {
    "name": "HVAC Repair (Past)",
    "id": 112683,
    "updated_at": "2014-11-05T15:00:40-05:00",
    "created_at": "2014-11-05T15:00:40-05:00",
    "url": "http://bidsketch.com/api/v1/templates/112683.json",
    "app_url": "http://hvactothefuture.bidsketch.com/proposaltemplates/112683/edit"
  },
  {
    "name": "HVAC Repair (Future)",
    "id": 112684,
    "created_at": "2014-11-05T15:01:09-05:00",
    "updated_at": "2014-11-05T15:01:09-05:00",
    "url": "http://bidsketch.com/api/v1/templates/112684.json",
    "app_url": "http://hvactothefuture.bidsketch.com/proposaltemplates/112684/edit"
  }
]
```

## Get Template

* `GET /templates/1.json` will get a single template
* `sections` and `fees` reference Account-level `Sections` and `Fees`
* Opening and closing sections are grouped together

```json
{
  "id": 112683,
  "name": "HVAC Repair (Past)",
  "created_at": "2014-11-05T15:00:40-05:00",
  "updated_at": "2015-01-07T12:12:40-05:00",
  "url": "http://bidsketch.com/api/v1/templates/112683.json",
  "app_url": "http://hvactothefuture.bidsketch.com/proposaltemplates/112683/edit",
  "sections": [
    {
      "url": "http://bidsketch.com/api/v1/sections/450451.json",
      "id": 450451,
      "name": "Frequently Asked Questions",
      "app_url": "http://hvactothefuture.bidsketch.com/sections/450451",
      "sectiontype": "closing"
    },
    {
      "url": "http://bidsketch.com/api/v1/sections/450449.json",
      "id": 450449,
      "name": "Our Advantage",
      "app_url": "http://hvactothefuture.bidsketch.com/sections/450449",
      "sectiontype": "opening"
    }
  ],
  "fees": [
    {
      "url": "http://bidsketch.com/api/v1/fees/187375.json",
      "id": 187375,
      "name": "Repairs",
      "app_url": "http://hvactothefuture.bidsketch.com/fees/187375",
      "feetype": "hourly"
    },
    {
      "url": "http://bidsketch.com/api/v1/fees/187371.json",
      "id": 187371,
      "name": "Time Travel",
      "app_url": "http://hvactothefuture.bidsketch.com/fees/187371",
      "feetype": "fixed"
    }
  ]
}
```
