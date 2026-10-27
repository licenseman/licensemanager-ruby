# LicenseManager::BillingPortalSession

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **url** | **String** | Link to the Stripe customer portal, to open right away: it expires shortly. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::BillingPortalSession.new(
  url: https://billing.stripe.com/p/session/test_YWNjdF8x
)
```

