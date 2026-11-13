# LicenseManager::PaddlePermission

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **resource** | **String** |  |  |
| **access** | **String** |  |  |
| **scope** | **String** | Permission of the Paddle API. |  |
| **reason** | **String** |  |  |
| **optional** | **Boolean** | Whether the key can connect without it, losing what it&#39;s for, explained by &#x60;reason&#x60;. |  |
| **subscriptions** | **Boolean** | Whether it&#39;s only needed to sell subscriptions: checked once a recurring price is mapped. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PaddlePermission.new(
  resource: Prices,
  access: null,
  scope: price.read,
  reason: Lists your prices so you can choose which ones create licenses, and checks they can still be paid.,
  optional: false,
  subscriptions: false
)
```

