# SKUs

## Get SKUs

```shell
curl "https://api.goods.co.uk/commerce/skus"
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
      "type": "sku",
      "relationships": {
        "sku-images": { "data": [] },
        "sku-fields": {
          "data": [{ "type": "sku-field", "id": "1" }]
        },
        "product": { "data": { "type": "product", "id": "1" } }
      },
      "attributes": { "stock-quantity": 9999, "price": 1999 }
    }
  ],
  "included": [
    {
      "type": "sku-field",

      "id": "1",
      "attributes": {
        "values": ["Blue T-shirt"],
        "slug": "name",
        "name": "Name"
      },
      "relationships": { "sku": { "data": { "type": "sku", "id": "1" } } }
    }
  ]
}
```

This endpoint retrieves all skus.

### HTTP Request

`GET https://api.goods.co.uk/commerce/skus`

### Query Parameters

| Parameter            | Type    | Description                       |
| -------------------- | ------- | --------------------------------- |
| filter[product_id]   | Integer | Filter by a specific product id   |
| filter[product_slug] | Integer | Filter by a specific product slug |

### Advanced SKU Field Filtering

SKUs can be filtered using their custom fields by constructing a more complex query.

This takes the form of an array of queries of the form `[slug][operator][value]` that is placed in the `filter[query]` parameter.

For example:

| Parameter          | Value          |
| ------------------ | -------------- |
| filter[query][0][] | "name"         |
| filter[query][0][] | "like"         |
| filter[query][0][] | "Blue T-shirt" |
| filter[query][1][] | "price"        |
| filter[query][1][] | "<="           |
| filter[query][1][] | "1000"         |
| filter[query][2][] | "is_favourite" |
| filter[query][2][] | "="            |
| filter[query][2][] | "true"         |

### Operators

The list of operators that be used in SKU field filtering.

| Operator          | Field types             | Description                        |
| ----------------- | ----------------------- | ---------------------------------- |
| like              | String                  | Case insensitive string comparison |
| =                 | Integer, Float, Boolean | Equality                           |
| <                 | Integer, Float          | Less than value                    |
| <=                | Integer, Float          | Less than or equal to value        |
| >                 | Integer, Float          | Greater than value                 |
| >=                | Integer, Float          | Greater than or euqal to value     |
| is_same           | Date                    | Date is equal to value             |
| is_before         | Date                    | Date is before value               |
| is_same_or_before | Date                    | Date is equal to or before value   |
| is_after          | Date                    | Date is after value                |
| is_same_or_after  | Date                    | Date is equal to or after value    |

## Get a Specific SKU

```shell
curl "https://api.goods.co.uk/commerce/skus/1"
  -H "Authorization: api_key"
  -d $'{}'
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": { "version": "1.0" },
  "id": "1",
  "attributes": { "stock-quantity": 9999, "price": 1999 },
  "data": {
    "type": "sku",
    "relationships": {
      "sku-images": { "data": [] },
      "sku-fields": {
        "data": [{ "type": "sku-field", "id": "1" }]
      },
      "product": { "data": { "type": "product", "id": "1" } }
    }
  },
  "included": [
    {
      "type": "sku-field",
      "relationships": { "sku": { "data": { "type": "sku", "id": "1" } } },
      "id": "1",
      "attributes": {
        "values": ["Blue T-shirt"],
        "slug": "name",
        "name": "Name"
      }
    }
  ]
}
```

This endpoint retrieves a specific SKU.

### HTTP Request

`GET https://api.goods.co.uk/commerce/skus/<ID>`

### URL Parameters

| Parameter | Description                   |
| --------- | ----------------------------- |
| ID        | The ID of the SKU to retrieve |
