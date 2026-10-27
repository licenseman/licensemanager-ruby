# LicenseManager::CancellationStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **license_count** | **Integer** | Number of licenses with a money back guarantee: a &#x60;cancellableUntil&#x60;. |  |
| **canceled_license_count** | **Integer** | Number of them that were canceled. |  |
| **cancellable_license_count** | **Integer** | Number of them whose money back guarantee hasn&#39;t ended, and that weren&#39;t canceled: they can still be. |  |
| **rate** | **Float** | Share of them that were canceled, from 0 to 1: &#x60;canceledLicenseCount&#x60; over &#x60;licenseCount&#x60;. |  |
| **canceled_by_day** | **Array&lt;Integer&gt;** | Number of them canceled each day, aligned on &#x60;days&#x60;, on the day of their cancellation. |  |
| **canceled_by_month** | **Array&lt;Integer&gt;** | Number of them canceled each month, aligned on &#x60;months&#x60;, on the month of their cancellation. |  |
| **by_reason** | [**Array&lt;CancellationStatsByReasonInner&gt;**](CancellationStatsByReasonInner.md) | Number of them canceled for each reason, from the most given one. Reasons never given are left out. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CancellationStats.new(
  license_count: 80,
  canceled_license_count: 4,
  cancellable_license_count: 12,
  rate: 0.05,
  canceled_by_day: [0, 1, 0],
  canceled_by_month: [1, 0, 2],
  by_reason: null
)
```

