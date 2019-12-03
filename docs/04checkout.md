---
tags: [04 - Docs]
---

# Checkout

When a merchant receives the "**access_token**" the next step is to send a "**POST**" request to the "**/api/v1/merchant/checkout**" route within the PayLata platform.

This request must have an "**Authorization**" header with a "**Bearer**" token set to the "**access_token**" received from the login request. Make sure the "**Accept**" header is set to "**application/json**" and "**Content-Type**" header is also set to "**application/json**".

We need the merchant to send as much details as possible about the customer including shopper information & statistics as it will help the automated credit decisioning process. The following is an example of the **JSON** request body:

```json
{
  "order": {
    "reference": "96865",
    "cart_reference": "34654645",
    "amount": 200.57,
    "currency": "SGD",
    "shipping": {
      "pickup": false,
      "tracking": {
        "uri": "string",
        "number": "string",
        "carrier": "string"
      },
      "address": {
        "line1": "1 George st",
        "line2": "string",
        "city": "string",
        "state": "NSW",
        "postal_code": "2000",
        "country": "AU",
        "first_name": "John",
        "last_name": "Doe"
      }
    },
    "items": [
      {
        "name": "string",
        "amount": 200.57,
        "reference": "string",
        "description": "string",
        "quantity": 0,
        "type": "string",
        "product_code": "string"
      }
    ]
  },
  "shopper": {
    "title": "string",
    "first_name": "string",
    "last_name": "string",
    "middle_name": "string",
    "phone": "string",
    "email": "user@example.com",
    "birth_date": "2017-11-21",
    "gender": "string",
    "billing_address": {
      "line1": "1 George st",
      "line2": "string",
      "city": "string",
      "state": "NSW",
      "postal_code": "2000",
      "country": "AU",
      "first_name": "John",
      "last_name": "Doe"
    },
    "statistics": {
      "account_created": "2017-11-21",
      "has_previous_purchases": true,
      "last_login": "2017-11-21",
      "currency": "SGD",
      "sales_total_count": 0,
      "sales_total_amount": 4500.00,
      "sales_avg_amount": 50.00,
      "sales_max_amount": 100.14,
      "refunds_total_amount": 100.23,
      "previous_chargeback": true
    }
  }
}
```

On success the response would return a JSON object with the "**checkout_id**" and "**uuid**":

```json
{
  "message": "Checkout record successfully created",
  "data": {
    "checkout_id": 3,
    "uuid": "JDTJHRDJD"
  }
}
```

The merchant will then redirect the customer to the PayLata platform with the "checkout_id" and "uuid" as parameters ("http://www.paylata.com/merchant/checkout/<checkout_id>/<uuid>").
