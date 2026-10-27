# LicenseManager::ProductStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **license_count** | **Integer** | Number of licenses of the product. |  |
| **active_license_count** | **Integer** | Number of licenses that haven&#39;t expired nor were canceled, and that a machine validated in the last 90 days. |  |
| **new_license_count** | **Integer** | Number of licenses created in the last 30 days, today included, in UTC. |  |
| **expiring_license_count** | **Integer** | Number of licenses expiring in the next 30 days, canceled ones left out. |  |
| **expired_license_count** | **Integer** | Number of licenses that expired in the last 30 days, canceled ones left out. |  |
| **active_machine_count** | **Integer** | Number of active machines of the licenses of the product. |  |
| **in_use_license_count** | **Integer** | Number of licenses with at least one active machine. |  |
| **seat_count** | **Integer** | Sum of the maximum numbers of machines of the licenses that haven&#39;t expired nor were canceled. Licenses without a maximum are left out. |  |
| **used_seat_count** | **Integer** | Number of active machines of the licenses counted in &#x60;seatCount&#x60;, at most their maximum number of machines each. |  |
| **full_license_count** | **Integer** | Number of licenses counted in &#x60;seatCount&#x60; active on their maximum number of machines. |  |
| **days** | **Array&lt;Date&gt;** | The 30 days covered by the daily stats, from the oldest one, in UTC. |  |
| **months** | **Array&lt;String&gt;** | The 12 months covered by the monthly stats, from the oldest one, in UTC. |  |
| **new_licenses_by_day** | **Array&lt;Integer&gt;** | Number of licenses created each day, aligned on &#x60;days&#x60;. |  |
| **new_licenses_by_month** | **Array&lt;Integer&gt;** | Number of licenses created each month, aligned on &#x60;months&#x60;. |  |
| **new_licenses_by_policy** | [**Array&lt;ProductStatsNewLicensesByPolicyInner&gt;**](ProductStatsNewLicensesByPolicyInner.md) | Number of licenses of each policy created each day and each month, for the policies with licenses created over the covered months. |  |
| **cancellation** | [**CancellationStats**](CancellationStats.md) | Cancellations of the licenses with a money back guarantee. &#x60;null&#x60; when no license of the product has one. |  |
| **revenue** | [**Array&lt;Revenue&gt;**](Revenue.md) | Revenue in each currency licenses were sold in, from the one with the most licenses sold. Amounts aren&#39;t converted between currencies. |  |
| **activations_by_version** | [**Array&lt;ProductStatsActivationsByVersionInner&gt;**](ProductStatsActivationsByVersionInner.md) | Successful activations of the licenses of the product each day, per version of the application, from the most recent one. |  |
| **active_machines_by_version** | [**Array&lt;ProductStatsActiveMachinesByVersionInner&gt;**](ProductStatsActiveMachinesByVersionInner.md) | Number of active machines running each version of the application, from the most recent one. |  |
| **active_machines_by_platform** | [**Array&lt;ProductStatsActiveMachinesByPlatformInner&gt;**](ProductStatsActiveMachinesByPlatformInner.md) | Number of active machines on each platform, from the one with the most machines. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStats.new(
  license_count: 120,
  active_license_count: 87,
  new_license_count: 14,
  expiring_license_count: 3,
  expired_license_count: 2,
  active_machine_count: 154,
  in_use_license_count: 80,
  seat_count: 200,
  used_seat_count: 130,
  full_license_count: 12,
  days: null,
  months: null,
  new_licenses_by_day: [0, 2, 1],
  new_licenses_by_month: [4, 9, 12],
  new_licenses_by_policy: null,
  cancellation: null,
  revenue: null,
  activations_by_version: null,
  active_machines_by_version: null,
  active_machines_by_platform: null
)
```

