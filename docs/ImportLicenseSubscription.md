# LicenseManager::ImportLicenseSubscription

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **provider** | **String** | Provider of the subscription. |  |
| **external_id** | **String** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ImportLicenseSubscription.new(
  provider: null,
  external_id: sub_1MowQVLkdIwHu7ix
)
```

