# LicenseManager::ConnectStripe

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **api_key** | **String** | Restricted API key of the Stripe account (&#x60;rk_live_…&#x60; for live products, &#x60;rk_test_…&#x60; for test products), with the &#x60;requiredPermissions&#x60; of &#x60;getStripeIntegration&#x60;. Without the optional ones, it connects with what they&#39;re for turned off. A secret key works too, but gives the app more access than it needs. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ConnectStripe.new(
  api_key: rk_live_51Nv0FG…
)
```

