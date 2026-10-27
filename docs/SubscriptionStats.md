# LicenseManager::SubscriptionStats

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **active_count** | **Integer** | Number of ongoing subscriptions: &#x60;active&#x60;, &#x60;trialing&#x60; or &#x60;past_due&#x60;. |  |
| **trialing_count** | **Integer** |  |  |
| **past_due_count** | **Integer** | Number of them whose renewal failed, as Stripe retries it: their licenses stay valid for the integration&#39;s grace days. |  |
| **canceling_count** | **Integer** | Number of them set to end at the end of their period. |  |
| **new_count** | **Integer** | Number of subscriptions started in the last 30 days. |  |
| **ended_count** | **Integer** | Number of subscriptions that ended in the last 30 days. |  |
| **churn_rate** | **Float** | Share of the subscriptions ongoing 30 days ago that ended since, from 0 to 1. |  |
| **new_by_month** | **Array&lt;Integer&gt;** | Number of subscriptions started each month, aligned on &#x60;months&#x60;. |  |
| **ended_by_month** | **Array&lt;Integer&gt;** | Number of subscriptions that ended each month, aligned on &#x60;months&#x60;. |  |
| **active_by_month** | **Array&lt;Integer&gt;** | Number of ongoing subscriptions at the end of each month, aligned on &#x60;months&#x60;, today for this month. |  |
| **mrr** | [**Array&lt;Mrr&gt;**](Mrr.md) | MRR in each currency, from the highest number of subscriptions. Amounts aren&#39;t converted between currencies. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::SubscriptionStats.new(
  active_count: 120,
  trialing_count: 4,
  past_due_count: 3,
  canceling_count: 5,
  new_count: 14,
  ended_count: 3,
  churn_rate: 0.025,
  new_by_month: [3, 5, 8],
  ended_by_month: [0, 1, 2],
  active_by_month: [90, 104, 120],
  mrr: null
)
```

