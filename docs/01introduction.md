---
tags: [Introduction]
---

# Introductions

The "**PayLata**" API is a REST based API that allows merchants to integrate PayLata into their web platform.

In order to use the API a merchant account must be created at <https://www.paylata.com> (Production platform) or <https://developer.paylata.com> (Sandbox platform). Create a new "**Express**" merchant record which will generate a "**Client Id**" and "**Secret Key**" which are needed to authenticate and generate "**access tokens**" that are used to access the various available endpoints.

![Merchant API client id and secret key](../assets/images/merchants1.png)

# Bank Account
A Bank account is required for each currency a merchant will accept within the platform. All fund deposits for a particular currency will be made to the default bank account linked to the respective currency.