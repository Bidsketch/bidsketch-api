# Proposals

Proposals are the bread and butter of Bidsketch. They are a collection of two different types of content: `Fees` and `Sections`. Proposals are owned by a single `User`, and meant for a single `Client`. 

## Get Proposals

* `GET /proposals.json` will return all the proposals for the account

```json
[
  {
    "id": 11051955,
    "url": "https://bidsketch.com/api/v1/proposals/11051955.json",
    "app_url": "https://hvactothefuture.bidsketch.com/proposals/11051955",
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "name": "HVAC repair for Mayor Wilson's Office.",
    "description": "We have the flux capacity to repair your HVAC system before it ever becomes a problem.",
    "status": "Pending",
    "is_draft": true
  },
  {
    "id": 10212015,
    "url": "https://bidsketch.com/api/v1/proposals/10212015.json",
    "app_url": "https://hvactothefuture.bidsketch.com/proposals/10212015",
    "created_at": "1985-10-25T11:35:23-08:00",
    "updated_at": "2015-10-21T13:04:17-08:00",
    "name": "HVAC repair for Mayor Wilson Jr.'s Office.",
    "description": "We have the flux capacity to repair your HVAC system before it ever becomes a problem.",
    "status": "Accepted",
    "is_draft": false
  }
]
```

## Get Proposal

* `GET /proposals/1.json` will get the proposal that has an `id` of 1

```json
{
  "id": 11051955,
  "url": "https://bidsketch.com/api/v1/proposals/11051955.json",
  "app_url": "https://hvactothefuture.bidsketch.com/proposals/11051955",
  "created_at": "1985-10-26T01:35:23-08:00",
  "updated_at": "1955-11-05T22:04:17-08:00",
  "proposal_dat": null,
  "name": "HVAC repair for Mayor Wilson's Office.",
  "description": "We have the flux capacity to repair your HVAC system before it ever becomes a problem.",
  "status": "Pending",
  "is_draft": true,
  "user": "Biff Tannen",
  "currency": "USD",
  "tax": 0,
  "tax2": 0,
  "monthly_fees": 1940,
  "yearly_fees": 1100,
  "one_time_fees": 4345,
  "discount": 0,
  "total": 7385,
  "settings": {
    "approval_message": "<p>Thanks!</p>",
    "hide_monthly_total": false,
    "optional_fees_note": "Note: Optional items are not included in proposal fees",
    "hide_project_total": false,
    "hide_yearly_total": false,
    "proposal_fees_title": "Fee Summary",
    "include_optional_fees_in_totals": true,
    "optional_fees_title": "Optional Items",
    "hide_grand_total": false
  },
  "client": {
    "id": 2927538,
    "name": "The Office of Mayor Goldie Wilson",
    "url": "https://bidsketch.com/api/v1/clients/2927538.json",
    "app_url": "https://hvactothefuture.bidsketch.com/clients/2927538"
  },
  "content": {
    "count": 11,
    "url": "http://bidsketch.com/api/v1/proposals/195980/content/195980.json",
    "opening_sections": {
      "count": 2,
      "url": "http://bidsketch.com/api/v1/proposals/195980/sections/opening.json"
    },
    "fees": {
      "count": 8,
      "url": "http://bidsketch.com/api/v1/proposals/195980/fees.json"
    },
    "closing_sections": {
      "count": 1,
      "url": "http://bidsketch.com/api/v1/proposals/195980/sections/closing.json"
    }
  }
}
```

## Get Proposal Content

* `GET /proposals/1/content.json` will get a proposal with all its content

The goal of proposals is to collect a bunch of content into a single document. It can be a bit cumbersome grabbing all that content using the normal RESTful methods, so use this method if you want to display the content all in one go. You'll get the content in two collections: `sections` and `fees`.

Be sure to keep content positioning in mind. Opening sections are grouped together first in the proposal, followed by fees, with closing sections finishing up the proposal. We will be simplifying positioning in the coming months, in a non-breaking way.

```json
{
  "id": 195980,
  "url": "http://bidsketch.com/api/v1/proposals/195980.json",
  "app_url": "http://hvactothefuture.bidsketch.com/proposal/195980",
  "content": {
    "opening_sections": [
      {
        "id": 1254193,
        "url": "http://bidsketch.com/api/v1/proposals/195980/sections/1254193.json",
        "name": "Testimonials",
        "description": "<p><em>\"The folks at HVAC to the Future are great!\"</em> - Scott Scottson</p>\n<p><em>\"When it comes to heating and air conditioner repair, those guys aren't chickens about getting the job done.\" </em>- Biff Tannen</p>"
      },
      {
        "id": 1254194,
        "url": "http://bidsketch.com/api/v1/proposals/195980/sections/1254194.json",
        "name": "Our Advantage",
        "description": "<p>We use <strong>science </strong>to our advantage to assess the problems with your HVAC system and go back in time to fix it as reliably as possible, before it becomes a problem.</p>"
      }
    ],
    "fees": [
      {
        "id": 620151,
        "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620151.json",
        "name": "Time Travel",
        "optional": false,
        "feetype": "fixed",
        "unit": null,
        "details": "$1,210",
        "currency": "USD",
        "amount": 1210.0,
        "quantity": null,
        "total": 1210.0,
        "description": "<p>We charge a low flat rate for time travel and materials involved. After all, plutonium is available in every corner store.</p>"
      },
      {
        "id": 620152,
        "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620152.json",
        "name": "Repairs",
        "optional": false,
        "feetype": "hourly",
        "unit": "Hour",
        "details": "$1,615 (19 hours @ $85/hour)",
        "currency": "USD",
        "amount": 85.0,
        "quantity": 19,
        "total": 1615.0,
        "description": "<p>For Mayor Wilson's Office, we estimate 19 hours of total work, across all timelines. This includes parts and materials.</p>",
      },
      {
        "id": 620153,
        "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620153.json",
        "name": "Paradox Protection",
        "optional": true,
        "feetype": "fixed",
        "unit": null,
        "details": "$400",
        "currency": "USD",
        "amount": 400.0,
        "quantity": null,
        "total": 400.0,
        "description": "<p>By going back in time to repair your HVAC system, we create a <em>slight </em>time paradox. With the optional Paradox Protection, we take steps to educate and inform your past self to ensure that our work does not interfere with the normal space-time continuum.</p>\n<p>Optional, but highly recommended.</p>"
      }
    ],
    "closing_sections": [
      {
        "id": 1254195,
        "url": "http://bidsketch.com/api/v1/proposals/195980/sections/1254195.json",
        "name": "Frequently Asked Questions",
        "description": "<p><em>\"How will I know it worked?\"</em></p>\n<p>Time travel is tricky. We will send you a signed certificate of completion via Western Union right now.</p>\n<p><em>\"While you're in the past, can you...?\"</em></p>\n<p>No.</p>\n<p><em>\"Not even this one favor?\"</em></p>\n<p>No.</p>\n<p><em>\"How does this work?\"</em></p>\n<p>Flux Capacitor.</p>"
      }
    ]
  }
}
```

## Create Proposal

* `POST /proposals.json` will create a proposal with the provided data

```json
{
  "name": "Auto Detailing for Mr. McFly",
  "description": "A wash and a coat of wax for a BMW 733i",
  "client_id": 163452
}
```

## Update Proposal

* `PUT /proposals/1.json` will update a specific proposal with the provided data

```json
{
  "description": "A wash and two coats of wax for a BMW 733i",
}
```

## Delete Proposal

* `DELETE /proposals/1.json` will delete a proposal, all it's content, and return `204 No Content`

## Proposal Sections

Proposal sections come in two flavors: `opening` and `closing`. Opening sections are presented first in a proposal, and closing sections are presented last. Not to be confused with top-level `Sections`, which are reusable section templates, proposal sections are unique to their proposal. When a `Proposal` is deleted, its sections are also deleted.

### Get Proposal Sections

* `GET /proposals/1/sections.json` will get a collection of sections for a proposal
* `GET /proposals/1/sections/opening.json` will list opening sections
* `GET /proposals/1/sections/closing.json` will list closing sections

```json
[
  {
    "id": 1235,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1235.json",
    "name": "Why You Can Trust Biff",
    "sectiontype": "opening"
  },
  {
    "id": 1231,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1231.json",
    "name": "Who Is This Biff Tannen?",
    "sectiontype": "opening"
  },
  {
    "id": 1237,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1237.json",
    "name": "Getting Your Car Back",
    "sectiontype": "closing"
  },
  {
    "id": 1234,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1234.json",
    "name": "Payment Options",
    "sectiontype": "closing"
  }
]
```

### Get Proposal Section

* `GET /proposals/1/sections/1.json` will fetch a single proposal section

```json
{
  "id": 1237,
  "created_at": "1985-10-26T01:35:23-08:00",
  "updated_at": "1955-11-05T22:04:17-08:00",
  "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1237.json",
  "name": "Getting Your Car Back",
  "sectiontype": "closing",
  "description": "<p>Getting your car back is actually really simple. All you have to do is pay the pickup fee.</p>"
}
```

### Create Proposal Section

* `POST /proposals/1/sections.json` will create a proposal section with the provided data

```json
{
  "name": "Our Disadvantage",
  "sectiontype": "opening",
  "description": "<p>We use <strong>science </strong>to our advantage to assess the problems with your HVAC system and go back in time to fix it as reliably as possible, before it becomes a problem.</p>"
}
```

### Update Proposal Section

* `PUT /proposals/1/sections/1.json` will update a proposal section with the provided data

```json
{
  "name": "Updated Name"
}
```

### Delete Proposal Section

* `DELETE /proposals/1/sections/1.json` will delete that proposal section

## Proposal Fees

Proposal Fees are a special type of content that contain information about costs associated with specific services.

### Get Proposal Fees

* `GET /proposals/1/fees` will list all the fees for a proposal

```json
[
  {
    "id": 620151,
    "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620151.json",
    "name": "Time Travel",
    "created_at": "2014-11-18T10:25:57-05:00",
    "updated_at": "2014-12-17T15:25:05-05:00",
    "total": 1210.0,
    "optional": false,
    "feetype": "fixed",
  },
  {
    "id": 620152,
    "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620152.json",
    "name": "Repairs",
    "created_at": "2014-11-18T10:30:28-05:00",
    "updated_at": "2014-12-17T15:25:05-05:00",
    "total": 1615.0,
    "optional": false,
    "feetype": "hourly"
  },
  {
    "id": 620153,
    "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620153.json",
    "name": "Paradox Protection",
    "created_at": "2014-11-18T10:37:16-05:00",
    "updated_at": "2014-12-17T15:25:05-05:00",
    "total": 400.0,
    "optional": true,
    "feetype": "fixed"
  }
]
```

### Get Proposal Fee

* `GET /proposals/1/fees/1.json` to get a single fee for a proposal

```json
{
  "id": 620151,
  "url": "http://bidsketch.com/api/v1/proposals/195980/fees/620151.json",
  "name": "Time Travel",
  "updated_at": "2014-12-17T15:25:05-05:00",
  "created_at": "2014-11-18T10:25:57-05:00",
  "feetype": "fixed",
  "optional": false,
  "currency": "USD",
  "total": 1210.0,
  "unit_amount": 1210.0,
  "details": "$1,210",
  "quantity": null,
  "unit": null,
  "description": "<p>We charge a low flat rate for time travel and materials involved. After all, plutonium is available in every corner store.</p>",
}
```

### Create Proposal Fee

* `POST /proposals/1/fees.json` will create a proposal fee with the provided data

```json
{
  "name": "Labor",
  "feetype": "hourly",
  "optional": false,
  "amount": 50,
  "quantity": 4,
  "description": "<p>We are not working for free.</p>"
}
```

### Update Proposal Fee

* `PUT /proposals/1/fees/1.json` will update a proposal fee with the provided data

```json
{
  "feetype": "custom",
  "amount": 8000,
  "quantity": 4,
  "unit": "Plutonium Stick"
}
```

### Delete Proposal Fee

* `DELETE /proposals/1/fees/1.json` will delete that proposal fee
