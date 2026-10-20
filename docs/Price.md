# LicenseManager::Price

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **amount** | **Float** | Amount in major units of the currency: &#x60;49.99&#x60; for $49.99, &#x60;5000&#x60; for ¥5,000. &#x60;0&#x60; for a free license. |  |
| **currency** | **String** | ISO 4217 code of the currency, in upper case. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Price.new(
  amount: 49.99,
  currency: USD
)
```

