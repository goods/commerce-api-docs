# Baskets

## Create a Basket

```shell
curl "https://api.goods.co.uk/commerce/baskets"
  -X "POST"
  -H 'Authorization: Bearer api_key'
  -d $'{"data": {}}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": { "version": "1.0" },
  "data": {
    "id": "12345678-1234-1234-1234-123456789012",
    "type": "basket",
    "relationships": {
      "shop": { "data": { "type": "shop", "id": "1" } },
      "basket-items": { "data": [] }
    },
    "attributes": { "total": 0, "quantity": 0 }
  }
}
```

This endpoint is used to create a basket

### HTTP Request

`POST https://api.goods.co.uk/commerce/baskets`

### Payload

The payload should be in [json-api](http://jsonapi.org) format.
