# LicenseManager::CreateIntegrationMapping

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **stripe_price_id** | **String** | Active one-time price of the Stripe account. |  |
| **policy_id** | **String** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreateIntegrationMapping.new(
  stripe_price_id: price_1MoBy5LkdIwHu7ix,
  policy_id: p4Rt8LmQ
)
```

