# Proposals

Proposals are the bread and butter of Bidsketch. They are a collection of two different types of content: `Fees` and `Sections`. Proposals are owned by a single `User`, and meant for a single `Client`. 

## Proposal Data

* Required attributes are **bold**.  
* Attributes required under certain conditions are _italic_.
* Attributes that can be set using `create` and `update` are marked with an asterisk(*)
* Nested attributes are indented below their parent with `>`

Attribute | Type | Info | Example
--------- | ---- | ---- | -------
**`name*`** | string | The proposal's name | `HVAC repair for Mayor Wilson's Office.`
**`client_id*`** | integer | The id for this proposal's client. **Note: This is returned in the client hash, but needs to be passed as `client_id` when creating or updating a proposal.**| `11051955`
`currency*` | string | An [ISO currency code](http://en.wikipedia.org/wiki/ISO_4217) that represents the proposal currency | `USD`
`description*` | text | A summary of the proposal | `We have the flux capacity to repair your HVAC system before it ever becomes a problem.`
`proposal_date*` | datetime or string | An optional attribute to set a specific date for the proposal. Returns a datetime string, but accepts '11/5/1955' when being set | October 26th, 1985 would be read as `1985-10-26T00:00:00-05:00` and set using `10/26/1985`
`tax*` | decimal | When reading, this value is the calculated tax amount. When setting, this should be a decimal that represents a percent. | a 10% tax would be read as `39.39` reading and set using `0.1`
`tax2*` | decimal | When reading, this value is the calculated secondary tax amount. When setting, this should be a decimal that represents a percent. | a 10% tax would be read as `39.39` reading and set using `0.1`
`discount*` | decimal | When reading, this value is the calculated discount amount. When setting, this should be a decimal that represents a percent. | a 10% discount would be read as `-39.39` reading and set using `0.1`
`settings*` | hash | A collection of proposal settings |
`> approval_message*` | html | The message sent to a client upon approval | `<p>Thanks!</p>`
`> optional_fees_note*` | string | A note displayed by optional items | `Note: Optional items are not included in proposal fees`
`> optional_fees_title*` | string | The heading used for the Optional Fee group | `Optional Items`
`> proposal_fees_title*` | string | The heading used for the Fee group | `Fee Summary`
`> include_optional_fees_in_totals*` | boolean | Should optional fees be included in totals? | `true`
`> hide_monthly_total*` | boolean | Should the monthly subtotal be hidden on the proposal? | `false`
`> hide_project_total*` | boolean | Should the project total be hidden on the proposal? | `false`
`> hide_yearly_total*` | boolean | Should the yearly subtotal be hidden on the proposal? | `false`
`> hide_grand_total*` | boolean | Should the grand total be hidden on the proposal? | `false`
`id` | integer | The unique id for the proposal | `11051955`
`url` | string | The API url for the proposal | `https://bidsketch.com/api/v1/proposals/11051955.json`
`app_url` | string | The Bidsketch app url for the proposal | `https://hvactothefuture.bidsketch.com/proposals/11051955`
`created_at` | datetime | When the proposal was created | `1985-10-26T01:35:23-08:00`
`updated_at` | datetime | When the proposal was last updated | `1955-11-05T22:04:17-08:00`
`status` | string | One of `Pending`, `Viewed`, `Accepted` or `Declined` | `Pending`
`is_draft` | boolean | Is the proposal a draft, or is it ready to be sent? | `true`
`user` | string | The name of the User who owns this proposal | `Biff Tannen`
`monthly_fees` | integer | The calculated monthly fee subtotal| `1940`
`yearly_fees` | integer | The calculated yearly fee subtotal | `1100`
`one_time_fees` | integer | The calculated fixed fee subtotal | `4345`
`total` | integer | The calculated proposal fee total | `7385`
`client` | hash | A collection of information about the proposal's client | {
`> id` | integer | The unique id for the proposal's client. Set using `client_id` | `2927538`
`> name` | string | The company or full name of the proposal's client | `The Office of Mayor Goldie Wilson`
`> url` | string | The API url for the proposal's client | `https://bidsketch.com/api/v1/clients/2927538.json`
`> app_url` | string | The Bidsketch app url for the proposal's client | `https://hvactothefuture.bidsketch.com/clients/2927538`
`content` | hash | A collection of information about the proposal's content | 
`> count` | integer | The number of the proposal's sections and fees  | `11`
`> url` | string | The API url for the proposal's content | `http://bidsketch.com/api/v1/proposals/195980/content/195980.json`
`> opening_sections` | hash | A collection of information about the proposal's opening sections | 
`>> count` | integer | The number of the proposal's opening sections | `2`
`>> url` | string | The API url to get the proposal's opening sections | `http://bidsketch.com/api/v1/proposals/195980/sections/opening.json`
`> fees` | hash | A collection of information about the proposal's fees | 
`>> count` | integer | The number of the proposal's fees | `8`
`>> url` | string | The API url to get the proposal's fees | `http://bidsketch.com/api/v1/proposals/195980/fees.json`
`> closing_sections` | hash | A collection of information about the proposal's closing sections |
`>> count` | integer | The number of the proposal's closing sections | `1`
`>> url` | string | The API url to get the proposal's closing sections | `http://bidsketch.com/api/v1/proposals/195980/sections/closing.json`

## Get Proposals

* `GET /proposals.json` will return all the proposals for the account
* `GET /clients/1/proposals.json` will return the proposals for a single client

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
  "proposal_date": null,
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
* `POST /templates/1/proposals.json` will create a proposal using an existing template with the provided data

```json
{
  "name": "Auto Detailing for Mr. McFly",
  "description": "A wash and a coat of wax for a BMW 733i",
  "client_id": 163452
}
```

### How to Create a Proposal from Scratch

The process of creating a fresh proposal with content through the API looks a little something like this:

1. Create a proposal with `POST /proposals.json` using at least a valid `name`, `description`, and `client_id`.
2. Create each proposal opening section with `POST /proposals/[the new proposal id]/sections.json` using at least a valid `name`, `description`, and "opening" `sectiontype`
3. Create each proposal fee with `POST /proposals/[new proposal id]/fees.json` using at least a valid `name`, `description`, `feetype`, and `amount`
4. Create each proposal closing section with `POST /proposals/[the new proposal id]/sections.json` using at least a valid `name`, `description`, and "closing" `sectiontype`

### How to Create a Proposal from a Template

You can also create a proposal from an existing template that will create proposal sections and proposal fees using the template

1. Create a proposal with `POST /templates/[the template id]/proposals.json` using at least a valid `name`, `description`, and `client_id`.
2. Create more proposal opening sections with `POST /proposals/[the new proposal id]/sections.json` using at least a valid `name`, `description`, and "opening" `sectiontype`
3. Create more proposal fees with `POST /proposals/[new proposal id]/fees.json` using at least a valid `name`, `description`, `feetype`, and `amount`
4. Create more proposal closing sections with `POST /proposals/[the new proposal id]/sections.json` using at least a valid `name`, `description`, and "closing" `sectiontype`

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

### Proposal Section Data

Proposal Section Data is the same as [Section Data](/sections/sections.md#section-data)

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

### Proposal Fee Data

Proposal Fee Data is the same as [Fee Data](/sections/fees.md#fee-data), with the addition of an **`optional*`** boolean flag.

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
