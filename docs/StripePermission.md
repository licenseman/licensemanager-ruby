# LicenseManager::StripePermission

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **resource** | **String** |  |  |
| **access** | **String** |  |  |
| **reason** | **String** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::StripePermission.new(
  resource: Prices,
  access: null,
  reason: Lists your prices so you can choose which ones create licenses, and checks they can still be paid.
)
```

