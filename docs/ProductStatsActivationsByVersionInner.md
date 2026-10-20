# LicenseManager::ProductStatsActivationsByVersionInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **version** | **String** | &#x60;null&#x60; for the activations that didn&#39;t send a version. |  |
| **counts** | **Array&lt;Integer&gt;** | Number of successful activations each day, aligned on &#x60;days&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStatsActivationsByVersionInner.new(
  version: 1.10.0,
  counts: [0, 3, 1]
)
```

