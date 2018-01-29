# Products

## Get Products

```shell
curl "https://api.goods.co.uk/commerce/products"
  -H "Authorization: api_key"
  -d $'{}'
```

> The above command returns JSON structured as JSON-API like this:

```json
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
```

This endpoint retrieves all products.

### HTTP Request

`GET https://api.goods.co.uk/commerce/products`

### Query Parameters

| Parameter     | Type   | Description                                                     |
| ------------- | ------ | --------------------------------------------------------------- |
| filter[slug]  | String | Filter the list of products by slug.                            |
| filter[query] | String | Return any products where a substring of name matches the query |

## Get a Specific Product

```shell
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
