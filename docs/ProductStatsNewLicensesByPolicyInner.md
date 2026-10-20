# LicenseManager::ProductStatsNewLicensesByPolicyInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **policy_id** | **String** |  |  |
| **by_day** | **Array&lt;Float&gt;** | Value each day, aligned on &#x60;days&#x60;. |  |
| **by_month** | **Array&lt;Float&gt;** | Value each month, aligned on &#x60;months&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStatsNewLicensesByPolicyInner.new(
  policy_id: p4Rt8LmQ,
  by_day: [0, 2, 1],
  by_month: [4, 9, 12]
)
```

