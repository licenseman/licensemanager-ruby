# LicenseManager::LicenseStatsActivationsByMachineInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **machine_id** | **String** |  |  |
| **name** | **String** |  |  |
| **fingerprint** | **String** |  |  |
| **counts** | **Array&lt;Integer&gt;** | Number of successful activations each day, aligned on &#x60;days&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseStatsActivationsByMachineInner.new(
  machine_id: m5Tq9HsJ,
  name: Jane&#39;s MacBook,
  fingerprint: 4c:32:75:8f:9a:1e,
  counts: [0, 3, 1]
)
```

