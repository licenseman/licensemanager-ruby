# LicenseManager::Mrr

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **currency** | **String** |  |  |
| **mrr** | **Float** | Monthly recurring revenue: the price of every ongoing subscription in the currency, times its quantity, brought to one month (a year counts for a twelfth), before taxes and discounts. |  |
| **by_interval** | [**Array&lt;MrrByIntervalInner&gt;**](MrrByIntervalInner.md) | Ongoing subscriptions and MRR of each billing period, like monthly and yearly, from the highest MRR. |  |
| **by_policy** | [**Array&lt;MrrByPolicyInner&gt;**](MrrByPolicyInner.md) | MRR of each policy, from the highest. |  |
| **by_month** | **Array&lt;Float&gt;** | MRR at the end of each month, aligned on &#x60;months&#x60;, today for this month, at the current prices of the subscriptions. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Mrr.new(
  currency: USD,
  mrr: 1240,
  by_interval: null,
  by_policy: null,
  by_month: [900, 1100, 1240]
)
```

