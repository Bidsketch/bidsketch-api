# Sections

Bidsketch users can save sections to their account to be reused in future proposals.

## Get Sections

* `GET /sections.json` will list all the sections saved to the account

```json
[
  {
    "id": 331684,
    "name": "Next Steps",
    "url": "http://bidsketch.com/api/v1/sections/331684.json",
    "app_url": "http://hvactothefuture.bidsketch.com/sections/331684",
    "created_at": "2013-08-05T15:39:00-04:00",
    "updated_at": "2013-08-14T18:09:34-04:00",
    "category": "Web Development",
    "sectiontype": "closing"
  },
  {
    "id": 450449,
    "name": "Our Advantage",
    "url": "http://bidsketch.com/api/v1/sections/450449.json",
    "app_url": "http://hvactothefuture.bidsketch.com/sections/450449",
    "created_at": "2015-01-05T13:00:19-05:00",
    "updated_at": "2015-01-05T17:11:34-05:00",
    "category": "HVAC Repair",
    "sectiontype": "opening"
  }
]
```

## Get Section

* `GET /sections/1.json` will fetch a section

```json
{
  "id": 450449,
  "name": "Our Advantage",
  "url": "http://bidsketch.com/api/v1/sections/450449.json",
  "app_url": "http://hvactothefuture.bidsketch.com/sections/450449",
  "category": "HVAC Repair",
  "created_at": "2015-01-05T13:00:19-05:00",
  "updated_at": "2015-01-05T17:11:34-05:00",
  "sectiontype": "opening",
  "description": "<p>We use <strong>science </strong>to our advantage to assess the problems with your HVAC system and go back in time to fix it as reliably as possible, before it becomes a problem.</p>"
}
```

## Create Section

* `POST /sections.json` will create a new section with the provided data

```json
{
  "name": "Our Disadvantage",
"sectiontype": "opening",
"description": "<p>We use <strong>science </strong>to our advantage to assess the problems with your HVAC system and go back in time to fix it as reliably as possible, before it becomes a problem.</p>"
}
```

## Update Section

* `PUT /sections/1.json` will update a section with the provided data

```json
{
  "name": "Our Advantage"
}
```

## Delete Section

* `DELETE /sections/1.json` will delete a section
