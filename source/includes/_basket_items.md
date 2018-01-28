# Basket items

## Create a Basket Item

```shell
curl "https://api.goods.co.uk/commerce/basket-items"
    -X "POST"
    -H 'Authorization: Bearer api_key'
    -d $'{
  "data": {
    "attributes": {
      "quantity": 1
    },
    "relationships": {
      "basket": {
        "data": {
          "id": "12345678-1234-1234-1234-123456789012",
          "type": "baskets"
        }
      },
      "sku": {
        "data": {
          "id": "1",
          "type": "skus"
        }
      }
    }
  }
}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": { "version": "1.0" },
  "data": {
    "id": "99999999-9999-9999-9999-999999999999",
    "type": "basket-item",
    "relationships": {
      "sku": { "data": { "type": "sku", "id": "1" } },
      "basket": {
        "data": {
          "type": "basket",
          "id": "12345678-1234-1234-1234-123456789012"
        }
      }
    },
    "attributes": {
      "quantity": 1,
      "price": 10000,
      "metadata": null,
      "is-hidden": false,
      "inserted-at": "2017-01-01T00:00:00.000000Z"
    }
  }
}
```

This endpoint is used to create a basket item

### HTTP Request

`POST https://api.goods.co.uk/commerce/basket-items`

### Payload

The payload should be in [json-api](http://jsonapi.org) format.

### Attributes

| Parameter | Required | Description                                       |
| --------- | -------- | ------------------------------------------------- |
| quantity  | yes      | The quantity of the SKU this basket item contains |

### Relationships

| Type | Required | Description                             |
| ---- | -------- | --------------------------------------- |
| sku  | yes      | The SKU that the basket item represents |
