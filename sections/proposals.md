# Proposals

Proposals are the bread and butter of Bidsketch. They are a collection of two different types of content: `Fees` and `Sections`. Proposals are owned by a single `User`, and meant for a single `Client`. 

## Get Proposals

* `GET /proposals.json` will return all the proposals for the account
* `GET /proposals/drafts.json` will return proposals that are still drafts

```json
[
  {
    "id": 11051955,
    "url": "https://bidsketch.com/api/v1/proposals/11051955.json",
    "app_url": "https://hvactothefuture.bidsketch.com/proposals/11051955",
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "project_name": "HVAC repair for Mayor Wilson's Office.",
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
    "project_name": "HVAC repair for Mayor Wilson Jr.'s Office.",
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
  "project_name": "HVAC repair for Mayor Wilson's Office.",
  "description": "We have the flux capacity to repair your HVAC system before it ever becomes a problem.",
  "status": "Pending",
  "is_draft": true,
  "user": "Biff Tannen",
  "client": {
    "id": 2927538,
    "name": "The Office of Mayor Goldie Wilson",
    "url": "https://bidsketch.com/api/v1/clients/2927538.json",
    "app_url": "https://hvactothefuture.bidsketch.com/clients/2927538"
  }, 
  "opening_sections": {
    "count": 4,
    "url": "https://bidsketch.com/api/v1/proposals/11051955/opening_sections.json",
    "app_url": "https://hvactothefuture.bidsketch.com/opening_sections/11051955"
  },
  "fees": {
    "count": 3,
    "url": "https://bidsketch.com/api/v1/proposals/11051955/fees.json",
    "app_url": "https://hvactothefuture.bidsketch.com/proposal_fees/11051955"
  },
  "closing_sections": {
    "count": 3,
    "url": "https://bidsketch.com/api/v1/proposals/11051955/closing_sections.json",
    "app_url": "https://hvactothefuture.bidsketch.com/closing_sections/11051955"
  },
}
```

## Create Proposal

* `POST /proposals.json` will create a proposal with the provided data

```json
{
  "project_name": "Auto Detailing for Mr. McFly",
  "description": "A wash and a coat of wax for a BMW 733i",
  "client_id": 163452
}
```

## Update Proposal

* `PUT /proposals/1.json` will update a specific proposal with the provided data

```json
{
  "description": "A wash and two coats of wax for a BMW 733i"
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
    "sectiontype": "opening",
    "position": 2,
    "description": "<h2>Biff&quot;s a good guy</h2><p>He&quot;s actually a really good guy.</p>"
  },
  {
    "id": 1231,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1231.json",
    "name": "Who Is This Biff Tannen?",
    "sectiontype": "opening",
    "position": 1,
    "description": "<p>Biff is an entrepreneur who has been looking after the community for a long time.</p>"
  },
  {
    "id": 1237,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1237.json",
    "name": "Getting Your Car Back",
    "sectiontype": "closing",
    "position": 1,
    "description": "<p>Getting your car back is actually really simple. All you have to do is pay the pickup fee.</p>"
  },
  {
    "id": 1234,
    "created_at": "1985-10-26T01:35:23-08:00",
    "updated_at": "1955-11-05T22:04:17-08:00",
    "url": "https://bidsketch.com/api/v1/proposals/11051955/sections/1234.json",
    "name": "Payment Options",
    "sectiontype": "closing",
    "position": 2,
    "description": "<p>I only accept cash.</p>"
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
  "position": 1,
  "proposal": {
    "id": 11051955,
    "url": "https://bidsketch.com/api/v1/proposals/11051955.json",
    "app_url": "https://hvactothefuture.bidsketch.com/proposals/11051955"
  },
  "description": "<p>Getting your car back is actually really simple. All you have to do is pay the pickup fee.</p>"
}
```

### Create Proposal Section

### Update Proposal Section

### Delete Proposal Section

## Proposal Fees

### Get Proposal Fees

### Get Proposal Fee

### Create Proposal Fee

### Update Proposal Fee

### Delete Proposal Fee

## Proposal Comments

### Get Proposal Comments

### Get Proposal Comment

### Create Proposal Comment

### Update Proposal Comment

### Delete Proposal Comment
