# LicenseManager::ProductStatsActiveMachinesByVersionInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **version** | **String** | &#x60;null&#x60; for the machines that didn&#39;t send a version. |  |
| **count** | **Integer** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStatsActiveMachinesByVersionInner.new(
  version: 1.10.0,
  count: 42
)
```

