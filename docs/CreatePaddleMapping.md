# LicenseManager::CreatePaddleMapping

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **paddle_price_id** | **String** | Active one-time or recurring catalog price of the Paddle account. |  |
| **policy_id** | **String** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreatePaddleMapping.new(
  paddle_price_id: pri_01gsz8x8sawmvhz1pv30nge1ke,
  policy_id: p4Rt8LmQ
)
```

