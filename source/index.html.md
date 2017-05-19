---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:

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

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
```

> Make sure to replace `64a26713b7d808be1c374a5b2e2b0b87` with your API key.

ReconAdvisor uses API keys to allow access to the API.

ReconAdvisor expects for the API key ID and API key to be included in all API requests to the server in a header that looks like the following for non user related requests:

`Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87`

Almost every request requires a user id and token to be included:

`Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87, access_token=1:fdd743cf0609a39794448f7200778257`

## Add User
> To authorize, use this code:

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
```

```shell
# With shell, you can just pass the correct header with each request
curl -X POST \
     -H "Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87" \
     -H "Content-Type: application/json" \
     -d '{"data":{"email":"paul@reconadvisor.com",
          "password": "64a26713b7d808be1c374a5b2e2b0b87",
          "confirmation_redirect_url":"http://google.com"}}' \
     https://api.reconadvisor.com/api/users
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
```

> Make sure to replace `64a26713b7d808be1c374a5b2e2b0b87` with your API key.

ReconAdvisor uses API keys to allow access to the API.

ReconAdvisor expects for the API key ID and API key to be included in all API requests to the server in a header that looks like the following for non user related requests:

`Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87`

Almost every request requires a user id and token to be included:

`Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87, access_token=1:fdd743cf0609a39794448f7200778257`




<aside class="notice">
You must replace <code>64a26713b7d808be1c374a5b2e2b0b87</code> with your personal API key.
</aside>

## User Login and Token generation
> To authorize, use this code:

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
```

```shell
# With shell, you can just pass the correct header with each request
curl -X POST \
     -H "Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87" \
     -H "Content-Type: application/json" \
     -d '{"data":{"email":"paul@reconadvisor.com",
          "password": "64a26713b7d808be1c374a5b2e2b0b87"}}' \
     http://localhost:3000/api/access_tokens -i
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
```

> Make sure to replace `64a26713b7d808be1c374a5b2e2b0b87` with your API key.

The token will be passed back from request and then every request from that point on should include the access_token below:cluded:

`Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87, access_token=1:fdd743cf0609a39794448f7200778257`




<aside class="notice">
You must replace <code>64a26713b7d808be1c374a5b2e2b0b87</code> with your personal API key.
</aside>

## Current Dealership or Multi Dealership User
> To authorize, use this code:

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
```

```shell
# With shell, you can just pass the correct header with each request
curl -X PATCH \
     -H "Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87, access_token=1:fdd743cf0609a39794448f7200778257" \
     -H "Content-Type: application/json" \
     -d '{"data":{"dealerships":"[TEST,DEVELOPMENT,TESTME3]","current_dealership":"TEST"}}' \
     http://localhost:3000/api/users/1
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
```

> Make sure to replace `64a26713b7d808be1c374a5b2e2b0b87` with your API key.

Every New User will have a default current_dealership so in their cases you will not need to update the current dealership.
However if the user has access to multiple stores the first action after logging in should always be to select a dealership by patching the users "current_dealership" setting.

Multisite users should also contain a dealerships array of each subdomain they have access to. This is a superadmin permission to set the first time but then is restricted to the dealerships in their group and their admin can add dealerships to their subsuers from the frontend users admin section.

Multisite users after logging in will have the option to select from any store.

`-d '{"data":{"dealerships":"[TEST,DEVELOPMENT,TESTME3]","current_dealership":"TEST"}}'`

<aside class="notice">
You must replace <code>64a26713b7d808be1c374a5b2e2b0b87</code> with your personal API key.
</aside>

## Setting Other Permissions
> To authorize, use this code:

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
```

```shell
# With shell, you can just pass the correct header with each request
curl -X PATCH \
     -H "Authorization: Cleanapi-Token api_key=1:64a26713b7d808be1c374a5b2e2b0b87, access_token=1:fdd743cf0609a39794448f7200778257" \
     -H "Content-Type: application/json" \
     -d '{"data":{"other_permissions":"create"}}' \
     https://api.reconadvisor.com/api/users/1
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
```

> Make sure to replace `64a26713b7d808be1c374a5b2e2b0b87` with your API key.

Set "other_permissions" by including them in an array.

`-d '{"data":{"other_permissions":"[create_vehicle,delete_vehicle,edit_vehicle]"}}'`

<aside class="notice">
You must replace <code>64a26713b7d808be1c374a5b2e2b0b87</code> with your personal API key.
</aside>

# Departments

## Get All Departments

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Departments Columns

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Department Permissions

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Department Notifications

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

# Vehicles

## Get All Vehicles

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: Cleanapi-Token api_key=1:my_api_key"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
let vehicles = api.vehicles.get();
```

> The above command returns JSON structured like this:

```json
[
  {"data":
    [
      {
        "stock":"A1234567",
        "vin":"123456789ABCDEFG",
        "year":2015,
        "make":"DODGE",
        "model":"CHALLENGER"
      },
      {
        "stock":"B1234567",
        "vin":"B23456789ABCDEFG",
        "year":2015,
        "make":"CHRYSLER",
        "model":"SEBRING"
      }
    ]
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
t.string :stock, index: true, unique: true
      t.string :vin, index: true, unique: true
      t.integer :year
      t.string :make, index: true
      t.string :model
      t.string :trim
      t.string :body
      t.string :stocktype, index: true
      t.string :color
      t.string :photocount
      t.string :currentdepartment, index: true
      t.string :previous_stocks
      t.timestamp :inventorydate, index: true
      t.timestamp :startdate, index: true
      t.timestamp :solddate, index: true
      t.boolean :deleted
      t.boolean :imported
      t.string :external_site
      t.integer :external_vid
      t.string :local_site
      t.integer :local_vid
      t.string :thumbnail
      t.integer :invoice
      t.integer :cost

      t.timestamps


<aside class="success">
Remember — a happy vehicle is an authenticated vehicle!
</aside>

## Get a Specific Vehicle

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get(2)
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get(2)
```

```shell
curl "https://api.reconadvisor.com/api/vehicles/2"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Sold Vehicles

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Used Vehicles

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All New Vehicles

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Vehicles in Department Currently

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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

## Get All Vehicles ever in Department

```ruby
require 'reconadvisor'

api = ReconAdvisor::APIClient.authorize!('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get
```

```python
import reconadvisor

api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87')
api.vehicles.get()
```

```shell
curl "https://api.reconadvisor.com/api/vehicles"
  -H "Authorization: 64a26713b7d808be1c374a5b2e2b0b87"
```

```javascript
const reconadvisor = require('reconadvisor');

let api = reconadvisor.authorize('64a26713b7d808be1c374a5b2e2b0b87');
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
