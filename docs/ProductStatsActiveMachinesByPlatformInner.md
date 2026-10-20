# LicenseManager::ProductStatsActiveMachinesByPlatformInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **platform** | **String** | &#x60;null&#x60; for the machines that didn&#39;t send a platform. |  |
| **count** | **Integer** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStatsActiveMachinesByPlatformInner.new(
  platform: macOS,
  count: 42
)
```

