# Example - create an order

> Step 1: create a basket

```shell
curl "https://api.goods.co.uk/commerce/baskets"
    -X "POST"
    -H 'Authorization: Bearer api_key'

    -d $'{"data": {}}'
```

> Step 2: create a basket item for SKU ID 1 and quantity 1

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
          "id": "26c266ee-9936-431a-8d3f-f4b3bc8f978f",
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

> Step 3: create an order from the basket with the customer's details

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
          "id": "26c266ee-9936-431a-8d3f-f4b3bc8f978f"
        }
      }
    }
  }
}
```

> Step 4: create a payment for the order using shop payment method 1

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

This is an example of how, from start to finish, a fully paid order can be created.

### Step 1: Create a basket

First up a basket must be created. Baskets can have items added and removed, be modified, etc.

### Step 2: Create a basket item

First up a basket must be created. Baskets can have items added and removed, be modified, etc.

### Step 3: Create an order from the basket

First up a basket must be created. Baskets can have items added and removed, be modified, etc.

### Step 4: Create a payment for the order

First up a basket must be created. Baskets can have items added and removed, be modified, etc.

In most cases the shop will be setup to automatically fulfil the order once the balance reaches zero.

<aside class="success">
It should be as easy as that!
</aside>
