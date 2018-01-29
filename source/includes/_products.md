# Products

## Get Products

```shell
curl "https://api.goods.co.uk/commerce/products"
  -H "Authorization: api_key"
<<<<<<< HEAD
=======
  -d $'{}'
>>>>>>> d45222f... Finish updating docs
```

> The above command returns JSON structured as JSON-API like this:

```json
<<<<<<< HEAD
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
=======
{
  "jsonapi": { "version": "1.0" },
  "data": [
    {
      "id": "1",
      "type": "product",
      "attributes": {
        "name": "T-shirt",
        "slug": "t-shirt",
        "description": "This is a really great T-shirt",
        "summary": "Great T-shirt"
      },
      "relationships": {
        "skus": {
          "data": [{ "type": "sku", "id": "1" }]
        },
        "product-fields": { "data": [] },
        "organisation": { "data": { "type": "organisation", "id": "1" } },
        "brand": { "data": { "type": "brand", "id": "1" } }
      }
    }
  ],
  "meta": { "total": 1 }
}
>>>>>>> d45222f... Finish updating docs
```

This endpoint retrieves all products.

### HTTP Request

`GET https://api.goods.co.uk/commerce/products`

### Query Parameters

<<<<<<< HEAD
| Parameter    | Default | Description                                                                      |
| ------------ | ------- | -------------------------------------------------------------------------------- |
| include_cats | false   | If set to true, the result will also include cats.                               |
| available    | true    | If set to false, the result will include kittens that have already been adopted. |

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>
=======
| Parameter     | Type   | Description                                                     |
| ------------- | ------ | --------------------------------------------------------------- |
| filter[slug]  | String | Filter the list of products by slug.                            |
| filter[query] | String | Return any products where a substring of name matches the query |
>>>>>>> d45222f... Finish updating docs

## Get a Specific Product

```shell
<<<<<<< HEAD
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
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

This endpoint retrieves a specific SKU.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                      |
| --------- | -------------------------------- |
| ID        | The ID of the kitten to retrieve |

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
const kittn = require("kittn");

let api = kittn.authorize("meowmeowmeow");
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the kitten to delete |
=======
curl "https://api.goods.co.uk/commerce/products/1"
  -H "Authorization: api_key"
  -d $'{}'
```

> The above command returns JSON structured as JSON-API like this:

```json
{
  "jsonapi": { "version": "1.0" },
  "data": {
    "id": "1",
    "type": "product",
    "attributes": {
      "name": "T-shirt",
      "slug": "t-shirt",
      "description": "This is a really great T-shirt",
      "summary": "Great T-shirt"
    },
    "relationships": {
      "skus": {
        "data": [{ "type": "sku", "id": "1" }]
      },
      "product-fields": { "data": [] },
      "organisation": { "data": { "type": "organisation", "id": "1" } },
      "brand": { "data": { "type": "brand", "id": "1" } }
    }
  }
}
```

This endpoint retrieves a specific product.

### HTTP Request

`GET https://api.goods.co.uk/commerce/products/<ID>`

### URL Parameters

| Parameter | Description                       |
| --------- | --------------------------------- |
| ID        | The ID of the product to retrieve |
>>>>>>> d45222f... Finish updating docs
