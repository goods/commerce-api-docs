# Orders

## Create an Order

```shell
curl "https://api.goods.co.uk/commerce/orders"
    -X "POST"
    -H 'Authorization: Bearer api_key'
    -d $'{
  "data": {
    "attributes": {
      "phone-number": "0123456789",
      "mobile-number": "",
      "billing-address1": "1 Infinite Loop",
      "billing-address2": "",
      "billing-city": "London",
      "billing-country": "GB",
      "email-address": "john@smith.com",
      "billing-region": "",
      "name": "John Smith",
      "billing-postcode": "W1 1AA"
    },
    "type": "orders",
    "relationships": {
      "basket": {
        "data": {
          "type": "baskets",
          "id": "12345678-1234-1234-1234-123456789012"
        }
      }
    }
  }
}
```

> The above command returns JSON structured like this:

```json
{
  "jsonapi": { "version": "1.0" },
  "data": {
    "id": "1234567890123",
    "type": "order",
    "attributes": {
      "total": 10000,
      "status": "reserved",
      "shipping-region": null,
      "shipping-postcode": null,
      "shipping-country": null,
      "shipping-city": null,
      "shipping-address2": null,
      "shipping-address1": null,
      "quantity": 1,
      "phone-number": "01234567890",
      "name": "John Smith",
      "mobile-number": null,
      "inserted-at": "2017-01-01T00:00:00.000000Z",
      "email-address": "john@smith.com",
      "billing-region": null,
      "billing-postcode": "W1 1AA",
      "billing-country": "GB",
      "billing-city": "London",
      "billing-address2": null,
      "billing-address1": "1 Infinite Loop",
      "balance": 10000,
      "amount-paid": 0
    },
    "relationships": {
      "shop": { "data": { "type": "shop", "id": "1" } },
      "payments": { "data": [] },
      "order-payment-methods": {
        "data": [{ "type": "order-payment-method", "id": "1" }]
      },
      "order-lines": {
        "data": [{ "type": "order-line", "id": "9876543210987" }]
      },
      "customer": { "data": { "type": "customer", "id": "1" } },
      "basket": {
        "data": {
          "type": "basket",
          "id": "12345678-1234-1234-1234-123456789012"
        }
      }
    }
<<<<<<< HEAD
  },
  "included": [
    {
      "id": "1",
      "type": "order-payment-method",
      "attributes": { "max-payable-amount": 10000 },
      "relationships": {
        "shop-payment-method": {
          "data": { "type": "shop-payment-method", "id": "1" }
        },
        "order": { "data": { "type": "order", "id": "1234567890123" } }
      }
    },
    {
      "id": "9876543210987",
      "type": "order-line",
      "attributes": {
        "status": "reserved",
        "quantity": 1,
        "price": 10000,
        "metadata": null,
        "is-hidden": false
      },
      "relationships": {
        "sku": { "data": { "type": "sku", "id": "1" } },
        "order": { "data": { "type": "order", "id": "1234567890123" } }
      }
    }
  ]
=======
  }
>>>>>>> d45222f... Finish updating docs
}
```

This endpoint is used to create an order

### HTTP Request

`POST https://api.goods.co.uk/commerce/orders`

### Payload

The payload should be in [json-api](http://jsonapi.org) format.

### Attributes

| Parameter         | Required | Description                                    |
| ----------------- | -------- | ---------------------------------------------- |
| name              | yes      | Customers full name                            |
| email-address     | yes      | Customer's email address                       |
| phone-number      | yes      | Customer's primary phone number                |
| mobile-number     | optional | Customer's mobile phone number                 |
| billing-address1  | yes      | Billing address first line                     |
| billing-address2  | optional | Billing address second line                    |
| billing-city      | yes      | Billing address city                           |
| billing-region    | optional | Billing address region (e.g. county or state)  |
| billing-postcode  | yes      | The postcode or zipcode                        |
| billing-country   | yes      | The two letter country code (e.g. GB)          |
| shipping-address1 | optional | Shipping address first line                    |
| shipping-address2 | optional | Shipping address second line                   |
| shipping-city     | optional | Shipping address city                          |
| shipping-region   | optional | Shipping address region (e.g. county or state) |
| shipping-postcode | optional | The postcode or zipcode                        |
| shipping-country  | optional | The two letter country code (e.g. GB)          |

### Relationships

| Type   | Required | Description                                      |
| ------ | -------- | ------------------------------------------------ |
| basket | yes      | The basket that the order should be created from |
<<<<<<< HEAD
=======

### Includes

As per the JSON API spec related resources can be included in the response payload. These can be requested by adding a parameter to request with the key `include` and the value as a comma separated list of the desired resources.

e.g. `include: "order_payment_methods,order_lines"`

| Type                  | Description                                                                                                                                                                |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| order_lines           | The order lines related to this order.                                                                                                                                     |
| order_payment_methods | The order payment methods available for this order. These will contain the `shop_payment_method` and the `max_payable_amount` that can be processed by that payment method |
>>>>>>> d45222f... Finish updating docs
