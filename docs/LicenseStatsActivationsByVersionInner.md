# LicenseManager::LicenseStatsActivationsByVersionInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **version** | **String** |  |  |
| **counts** | **Array&lt;Integer&gt;** | Number of successful activations each day, aligned on &#x60;days&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseStatsActivationsByVersionInner.new(
  version: null,
  counts: [0, 3, 1]
)
```

