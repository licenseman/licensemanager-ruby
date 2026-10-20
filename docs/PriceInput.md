# LicenseManager::PriceInput

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **amount** | **Float** | Amount in major units of the currency: &#x60;49.99&#x60; for $49.99, &#x60;5000&#x60; for ¥5,000. &#x60;0&#x60; for a free license. At most as many decimals as the currency&#39;s minor unit: 2 for USD, 0 for JPY. |  |
| **currency** | **String** | ISO 4217 code of the currency, in upper case. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PriceInput.new(
  amount: 49.99,
  currency: USD
)
```

