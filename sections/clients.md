# Clients

Clients are the folks or companies that Bidsketch customers are preparing proposals for.

## Get Clients

* `GET /clients.json` will return all the clients on the account

```json
[
  {
    "id": 4815162342,
    "url": "https://bidsketch.com/api/v1/clients/4815162342.json",
    "app_url": "https://ericsgazebos.bidsketch.com/clients/4815162342",
    "created_at": "2014-04-08T15:16:23-05:00",
    "updated_at": "2014-05-12T12:45:01-05:00",
    "first_name": "Eric",
    "last_name": "Steele",
    "name": "Eric's Gazebo Emporium",
    "phone": "481-516-2342",
    "email": "eric@bidsketch.com"
  },
  {
    "id": 23007,
    "url": "https://bidsketch.com/api/v1/clients/23007.json",
    "app_url": "https://ericsgazebos.bidsketch.com/clients/23007",
    "created_at": "2014-10-23T15:16:23-05:00",
    "updated_at": "2014-10-24T12:45:01-05:00",
    "first_name": "James",
    "last_name": "Bond",
    "name": "Universal Exports",
    "phone": "+44 03069 007007",
    "email": "jbond@universalexports.co.uk"
  }
]
```

## Get Client

* `GET /clients/1.json` will get the client whose `id` is 1

```json
{
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
```

## Get Client Proposals

* `GET /clients/1/proposals.json` will get a collection of all the proposals for a single client

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

## Create Client

* `POST /clients.json` will create a client using the provided data.

```json
{
  "first_name": "Ferris",
  "last_name": "Bueller",
  "email": "ferris@saveferris.org"
}
```

A successful response will return the new client formatted just like a *Get Client* request with a `201 Created` status.

If unsuccessful, this will return a `400 Bad Request` status with an array of errors.

Some plans have limits to the number of clients that can be created. If that limit has been reached, the request will return with a `426 Upgrade Required` status and details about limit.

## Update Client

* `PUT /clients/1.json` will update a client using the provided data.

```json
{
  "first_name": "Jimmy",
  "last_name": "Bond"
}
```

If successful, this will return `200 OK` along with the updated JSON representation of the client.

If unsuccessful, this will return a `400 Bad Request` status with an array of errors.

## Delete Client

* `DELETE /clients/1.json` will delete a client and return `204 No Content`
* Keep in mind this will delete all the Proposals for a client.

