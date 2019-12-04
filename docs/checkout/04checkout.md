---
tags: [Checkout]
---

# 01 - Execute Checkout Request

When a merchant receives an "**access_token**" the next step is to send a "**POST**" request to the "**/api/v1/merchant/checkout**" route within the PayLata platform.

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
        "uri": "https://www.amazon.com/progress-tracker/package/ref=ppx_yo_dt_b_track00",
        "number": "0865086508GSFS",
        "carrier": "Amazon"
      },
      "address": {
        "line1": "1 George st",
        "line2": "",
        "city": "Sydney",
        "state": "NSW",
        "postal_code": "2000",
        "country": "AU",
        "first_name": "John",
        "last_name": "Doe"
      }
    },
    "items": [
      {
        "name": "Samsung Earbuds",
        "amount": 200.57,
        "reference": "",
        "description": "True Wireless Earbuds, Black",
        "quantity": 1,
        "type": "sku",
        "product_code": "samsung_earbud_01"
      }
    ]
  },
  "shopper": {
    "title": "Mr",
    "first_name": "John",
    "last_name": "Doe",
    "middle_name": "",
    "phone": "186598698",
    "email": "johndoe@example.com",
    "birth_date": "1997-11-21",
    "gender": "male",
    "billing_address": {
      "line1": "1 George st",
      "line2": "",
      "city": "Sydney",
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
      "sales_total_count": 5,
      "sales_total_amount": 4500.00,
      "sales_avg_amount": 50.00,
      "sales_max_amount": 100.14,
      "refunds_total_amount": 100.23,
      "previous_chargeback": true
    }
  }
}
```

On success a JSON response will be returned with a "**checkout_id**" and "**uuid**":

```json
{
  "message": "Checkout record successfully created",
  "data": {
    "checkout_id": 3,
    "uuid": "JDTJHRDJD"
  }
}
```

The merchant will then redirect the customer to the PayLata platform using the "**checkout_id**" and "**uuid**" as parameters ("<http://www.paylata.com/merchant/3/JDTJHRDJD"). See the "**Redirect to PayLata**" page for more details.
