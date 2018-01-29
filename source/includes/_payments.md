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
  "id": "abcdef12-abcd-abcd-abcd-abcdef123456",
  "data": {
    "type": "payment",
    "relationships": {
      "shop-payment-method": {
        "data": { "type": "shop-payment-method", "id": "1" }
      },
      "order": { "data": { "type": "order", "id": "1234567891234" } }
    },
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

### Includes

As per the JSON API spec related resources can be included in the response payload. These can be requested by adding a parameter to request with the key `include` and the value as a comma separated list of the desired resources.

e.g. `include: "order,order.order_payment_methods"`

| Type                        | Description                                                                                                                                                                       |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| order                       | The order linked to the payment.                                                                                                                                                  |
| order.order_payment_methods | The updated order payment methods available for this order. Each order payment method will have had its `amount_payable` adjusted now that at least one payment has been created. |
