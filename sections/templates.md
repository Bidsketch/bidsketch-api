# Proposal Templates

One of our customers' favorite features is the ability to save proposal templates that can be used as a starting point for new proposals. We're working on overhauling how templates work, so for now the API only exposes the ability to list existing templates and view specific templates.

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
