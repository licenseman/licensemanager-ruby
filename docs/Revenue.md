# LicenseManager::Revenue

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **currency** | **String** | ISO 4217 code of the currency of the revenue. |  |
| **license_count** | **Integer** | Number of licenses sold in the currency, free ones included, canceled ones left out. |  |
| **total** | **Float** | Sum of the prices of the licenses sold in the currency, in major units, canceled ones left out. |  |
| **canceled_license_count** | **Integer** | Number of canceled licenses sold in the currency. |  |
| **canceled_total** | **Float** | Sum of the prices of the canceled licenses sold in the currency, in major units: revenue lost to cancellations. |  |
| **this_month** | **Float** | Revenue of the current month, in UTC. |  |
| **last_month** | **Float** | Revenue of the previous month, in UTC. |  |
| **last30_days** | **Float** | Revenue of the last 30 days, today included, in UTC. |  |
| **by_day** | **Array&lt;Float&gt;** | Revenue each day, aligned on &#x60;days&#x60;. |  |
| **by_month** | **Array&lt;Float&gt;** | Revenue each month, aligned on &#x60;months&#x60;. |  |
| **by_policy** | [**Array&lt;ProductStatsNewLicensesByPolicyInner&gt;**](ProductStatsNewLicensesByPolicyInner.md) | Revenue of the licenses of each policy, for the policies with licenses sold in the currency over the covered months. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Revenue.new(
  currency: USD,
  license_count: 42,
  total: 2099.58,
  canceled_license_count: 2,
  canceled_total: 99.98,
  this_month: 349.93,
  last_month: 299.94,
  last30_days: 399.92,
  by_day: [0, 49.99, 99.98],
  by_month: [199.96, 249.95, 349.93],
  by_policy: null
)
```

