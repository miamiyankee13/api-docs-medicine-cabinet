---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell


toc_footers:
  - <a href='https://github.com/miamiyankee13/medicine-cabinet'>View Medicine Cabinet on GitHub</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Medicine Cabinet API! You can use our API to access Medicine Cabinet API endpoints, which can interact with our database of medicinal cannabis strains, as well as manage your digital medicine cabinet.

# Registration
> To register with Medicine Cabinet, use this code:

```shell
curl -X POST
  https://medicine-cabinet.herokuapp.com/users
  -H 'Content-Type: application/json'
  -d '{
	"userName": "<your username>",
	"password": "<your password>",
	"firstName": "<your first name>",
	"lastName": "<your last name>"
}'
```
Medicine Cabinet uses JSON Web Token (JWT) to conrol access to the API. To obtain a token, you must have an account. To create an account, you can either register from the client side or make a POST request to the `users` endpoint.

### HTTP Request

`POST https://medicine-cabinet.herokuapp.com/users`

### Required Fields
Field | Description
----- | -----------
userName | Your desired username
password | Your desired password
firstName | Your first name
lastName | Your last name

If successful, you should see a 201 response code.

# Authentication

> To obtain a token, use this code:

```shell
curl -X POST 
  https://medicine-cabinet.herokuapp.com/auth/login
  -H 'Content-Type: application/json'
  -d '{
	"userName": "<your username>",
	"password": "<your password>"
}'
```
Once you have an account, you must make a POST request to this endpoint in order to obtain a token.

### HTTP Request

`https://medicine-cabinet.herokuapp.com/auth/login`

### Required Fields
Field | Description
----- | -----------
userName | Your username
password | Your password

If successful, this endpoint will return a 7 day expiry token. This token must be added in the header of any requests to protected endpoints via Bearer Authentication. The header should look as follows:

`Authorization: Bearer <token>`

<aside class="notice">
You must replace <code>&lt;token&gt;</code> with your token.
</aside>




# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
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

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

