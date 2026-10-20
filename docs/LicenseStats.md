# LicenseManager::LicenseStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **from** | **Date** | First day covered, in UTC. |  |
| **to** | **Date** | Last day covered, in UTC: today. |  |
| **days** | **Array&lt;Date&gt;** | The 90 days covered, from the oldest one, in UTC. |  |
| **activations_by_machine** | [**Array&lt;LicenseStatsActivationsByMachineInner&gt;**](LicenseStatsActivationsByMachineInner.md) | Machines that activated the license in the period, from the one with the most activations. |  |
| **activations_by_version** | [**Array&lt;LicenseStatsActivationsByVersionInner&gt;**](LicenseStatsActivationsByVersionInner.md) | Versions of the application that activated the license in the period, from the most recent one. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseStats.new(
  from: 2026-10-12,
  to: 2026-10-12,
  days: null,
  activations_by_machine: null,
  activations_by_version: null
)
```

