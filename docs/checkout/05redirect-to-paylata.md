---
tags: [Checkout]
---

# 02 - Redirect to PayLata

After receiving the "**checkout_id**" and "**uuid**" the merchant will then redirect the customer to the PayLata platform using the "**checkout_id**" and "**uuid**" as parameters (https://paylata.com/merchant/checkout/<**checkout_id**>/<**uuid**>).

## Login

If the customer is not logged in, they will be redirected to the PayLata "**Login**" page. If they have an account they will log in and then be redirected to the details page to complete the PayLata process for the order they started on the merchant's website site. If they are already logged in they will automatically be redirected to the details page to complete the PayLata process.

## Register
If the customer does not have an account they will have to click the "**Register**" link/button to create an account and they would go through the automated approval process. Once registration is complete and account approved they will be redirected to the details page to complete the PayLata process. If the account is not approved they will be redirected back to the merchant's website with the respective error code and message.

## Credit Limit
Once a user's account is approved a check is done to see if the amount to be paid will take the customer over their "**Credit Limit**". If the amount won't take them over their credit limit an Invoice will be created and the customer redirected to the invoice details page which shows the details of the purchase including the total to be paid.

## Complete PayLata Process
On the invoice details page the user will enter their credit card information and submit the form. The response to the customer will be dependent on the response from the credit card processor or if any validation or system errors occur.

If successful, a payment schedule will be created and customer will be redirected back to the merchant website using the "**redirect**" url set for the merchant record. The "**checkout_id**", "**checkout_uuid**" and newly generated "**invoice_id**" will be added as parameters in the form (**?checkout_id=<checkout_id>&checkout_uuid=<checkout_uuid>&invoice_id=<invoice_id>**). 
