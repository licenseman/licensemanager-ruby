# LicenseManager::UpdateIntegration

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **auto_refund** | **Boolean** | Whether canceling a license bought through Stripe refunds its payment. Can only be turned on when the integration&#39;s &#x60;canRefund&#x60; is true: the API key has the Refunds: Write permission. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateIntegration.new(
  auto_refund: false
)
```

