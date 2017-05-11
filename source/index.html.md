---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Recon Advisor API! This is a work in progress so please feel free to contact us with any suggestions or comments. Thanks!

# Authentication

> To authorize, use this code:

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('meowmeowmeow')
```

```python
import reconadvisor

api = reconadvisor.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

ReconAdvisor uses API keys to allow access to the API. You can register a new ReconAdvisor API key at our [developer portal](https://api.reconadvisor.com/developers).

ReconAdvisor expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Vehicles

## Get All Vehicles

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('meowmeowmeow')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('meowmeowmeow')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: meowmeowmeow"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('meowmeowmeow');
let vehicles = api.vehicles.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all vehicles.

### HTTP Request

`GET https://api.reconadvisor.com/api/vehicles`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include vehicles that have already been adopted.

<aside class="success">
Remember — a happy vehicle is an authenticated vehicle!
</aside>

## Get a Specific Vehicle

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('meowmeowmeow')
api.vehicles.get(2)
```

```python
import reconadvisor

api = reconadvisor.authorize('meowmeowmeow')
api.vehicles.get(2)
```

```shell
curl "https://api.reconadvisor.com/api/vehicles/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('meowmeowmeow');
let max = api.vehicles.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific vehicle.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.reconadvisor.com/vehicles/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the vehicle to retrieve

