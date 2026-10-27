# LicenseManager::MrrByIntervalInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **interval** | **String** |  |  |
| **interval_count** | **Integer** |  |  |
| **subscription_count** | **Integer** |  |  |
| **mrr** | **Float** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::MrrByIntervalInner.new(
  interval: null,
  interval_count: 1,
  subscription_count: 80,
  mrr: 800
)
```

