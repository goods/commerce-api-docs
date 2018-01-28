# Payments

## Create a Payment

```shell
curl "https://api.goods.co.uk/commerce/payments"
    -X "POST"
    -H 'Authorization: Bearer api_key'

    -d $'{
  "data": {
    "attributes": {
      "amount": "10000",
      "capture": "true"
    },
    "relationships": {
      "order": {
        "data": {
          "type": "orders",
          "id": "1234567891234"
        }
      },
      "shop-payment-method": {
        "data": {
          "type": "shop-payment-methods",
          "id": "1"
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
  "included": [
    {
      "type": "order-payment-method",
      "relationships": {
        "payment-method": { "data": { "type": "payment-method", "id": "2" } },
        "order": { "data": { "type": "order", "id": "1617281418911" } }
      },
      "id": "33",
      "attributes": { "max-payable-amount": 0 }
    },
    {
      "type": "order",
      "relationships": {
        "shop": { "data": { "type": "shop", "id": "2" } },
        "payments": {
          "data": [
            { "type": "payment", "id": "157dc890-1613-46b1-991d-d1db2cd61473" }
          ]
        },
        "order-payment-methods": {
          "data": [{ "type": "order-payment-method", "id": "1" }]
        },
        "order-lines": {
          "data": [{ "type": "order-line", "id": "1617281419128" }]
        },
        "customer": { "data": { "type": "customer", "id": "1" } },
        "basket": {
          "data": {
            "type": "basket",
            "id": "26c266ee-9936-431a-8d3f-f4b3bc8f978f"
          }
        }
      },
      "id": "1617281418911",
      "attributes": {
        "total": 10000,
        "status": "dispatched",
        "shipping-region": null,
        "shipping-postcode": null,
        "shipping-country": null,
        "shipping-city": null,
        "shipping-address2": null,
        "shipping-address1": null,
        "quantity": 1,
        "phone-number": "01753622331",
        "name": "Test",
        "mobile-number": null,
        "inserted-at": "2018-01-19T16:43:02.228667Z",
        "email-address": "kyle@wearelion.com",
        "billing-region": null,
        "billing-postcode": "SL4 3BP",
        "billing-country": "GB",
        "billing-city": "Windsor",
        "billing-address2": null,
        "billing-address1": "21a",
        "balance": 0,
        "amount-paid": 10000
      }
    }
  ],
  "data": {
    "type": "payment",
    "relationships": {
      "payment-method": { "data": { "type": "payment-method", "id": "4" } },
      "order": { "data": { "type": "order", "id": "1617281418911" } }
    },
    "id": "157dc890-1613-46b1-991d-d1db2cd61473",
    "attributes": { "token": null, "amount": 10000 }
  }
}
```

This endpoint is used to create a payment

### HTTP Request

`POST https://api.goods.co.uk/commerce/payments`

### Payload

The payload should be in [json-api](http://jsonapi.org) format.

### Attributes

| Parameter    | Required | Description                                |
| ------------ | -------- | ------------------------------------------ |
| amount       | yes      | The amount to be paid                      |
| capture      | yes      | Take payment immediately or just authorize |
| card-number  | optional | Full card number                           |
| cardholder   | optional | Card holders full name                     |
| valid-from   | optional | Card valid from date (e.g. 0117)           |
| expiry-date  | optional | Card expiry date (e.g. 0120)               |
| issue-number | optional | Card issue number                          |
| cvv          | optional | CVV card security code                     |
| token        | optional | Token payment string                       |

### Relationships

| Type                | Required | Description                                    |
| ------------------- | -------- | ---------------------------------------------- |
| order               | yes      | The order linked to the payment                |
| shop-payment-method | yes      | The shop payment method to use for the payment |
