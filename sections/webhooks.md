# Webhooks

We make webhook notifications available for important events in the Bidsketch application.

* We `POST` data
* You need to respond with a `200 OK` HTTP response.
* If we don't receive a `200 OK` response, we will retry 20 times.
* After 20 attempts, we email the Bidsketch account admin that something is wrong with the notification.
* If a response is `410 Gone` then we delete the webhook.

## Webhook Events

Event | Info | Data
----- | ---- | ----
`client_created` | Triggered when a client is created through the API or in the Bidsketch app | [Client Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/clients.md#client-data)
`proposal_created` | Triggered when a proposal is created through the API or saved for the first time in the Bidsketch app | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)
`proposal_sent` | Triggered each time a proposal is sent to a client | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)
`proposal_viewed` | Triggered each time a proposal is viewed by a client | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)
`proposal_accepted` | Triggered when a proposal is accepted by a client or Bidsketch user | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)
`proposal_declined` | Triggered when a proposal is declined by a client or Bidsketch user | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)
`proposal_accepted_or_declined` | Triggered when a proposal is either accepted or declined by a client or Bidsketch user | [Proposal Attributes](https://github.com/Bidsketch/bidsketch-api/blob/master/sections/proposals.md#proposal-data)

## Webhook Payloads

When a webhook is triggered, we POST a JSON-formatted body with `event` and `data` keys. `event` is the event being triggered and `data` is the JSON-formatted object for the subject of the event.

```json
{
  "event": "client_created",
  "data": {
    "id": 4815162342,
    "url": "https://bidsketch.com/api/v1/clients/4815162342.json",
    "app_url": "https://ericsgazebos.bidsketch.com/clients/4815162342",
    "created_at": "2014-04-08T15:16:23-05:00",
    "updated_at": "2014-05-12T12:45:01-05:00",
    "first_name": "Eric",
    "last_name": "Steele",
    "name": "Eric's Gazebo Emporium",
    "phone": "481-516-2342",
    "email": "eric@bidsketch.com",
    "alt_phone": "1-800-GAZEBOS",
    "website": "ericsgazeboemporium.com",
    "address_field_one": "1 Gazebo Way",
    "address_field_two": "Gazebo Suite",
    "city": "Philadelphia",
    "state": "PA",
    "postal_zip": "19106",
    "country": "USA",
    "notes": "Calls himself \"The King of Gazebos\"",
    "other_contact": {
      "phone": "867-5309",
      "first_name": "Jenny",
      "last_name": "Tutone",
      "email": "jenny@bidsketch.com"
    }
  }
}
```

## Create Webhook

* `POST /webhooks.json` will create a webhook using the provided data.
* `event` and `endpoint` are the only options and are required.

```json
{
  "event": "client_created",
  "endpoint": "http://bidsketch.com/a-fake-webhook-endpoint"
}
```

If successful, this will return `200 OK` along with a JSON representation of the webhook:

```json
{
  "id": 1,
  "event": "proposal_created",
  "endpoint": "http://requestb.in/14imao61",
  "created_at": "2015-03-24T16:48:36-04:00",
  "updated_at": "2015-03-24T16:48:36-04:00",
  "url": "http://bidsketch.com/api/v1/webhooks/1.json"
}
```

Make sure to store the id or url of the newly created webhook so you can delete it later on.

## Delete Webhook

* `DELETE /webhooks/1.json` will delete a webhook and return `204 No Content`
