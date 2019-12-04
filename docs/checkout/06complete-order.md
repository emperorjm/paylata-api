---
tags: [Checkout]
---

# 03 - Complete PayLata Order

The customer will be redirected back to the merchant website using the "**redirect**" url set for the merchant record the secret key is linked to. The "**checkout_id**", "**checkout_uuid**" and "**invoice_id**" will be added as parameters in the form (**?checkout_id=<checkout_id>&checkout_uuid=<checkout_uuid>&invoice_id=<invoice_id>**). After redirecting back to the Merchant’s website the merchant still needs to execute one final call to check the final status of the PayLata process which will determine if the customer's order should be completed or not.

The merchant should generate a new "**access token**" to make sure that a valid token is used to access the next route as we don't know how long the customer will take before being redirected back to the merchant's website as the previous access token might expire. The merchant should then send a "**POST**" request to "**api/v1/merchant/checkout/complete**" with the following JSON data object:

```json
{
	"checkout_id": 2,
	"checkout_uuid": "JQVJRMU5JKWZ3S2MEFUKDZTFR",
	"invoice_id": 7
}
```

If there are no errors a "**Success**" message will be sent back to the merchant with a status of "**200**" stating that the PayLata process was completed successfully and the funds will be deposited to the merchant's default bank account linked to the order currency within 48hrs. The merchant can then complete the customer's order within their platform.
