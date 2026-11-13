# LicenseManager::LicenseSubscription

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **provider** | **String** | Provider of the subscription. |  |
| **external_id** | **String** | Id of the subscription in the provider: &#x60;sub_…&#x60; in Stripe and in Paddle. |  |
| **stripe_subscription_id** | **String** | Deprecated: use &#x60;externalId&#x60;, which it equals. |  |
| **status** | **String** | Status of the subscription in the provider. Stripe: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60; while a failed payment is retried, &#x60;canceled&#x60;, &#x60;unpaid&#x60;, &#x60;paused&#x60;, &#x60;incomplete&#x60; or &#x60;incomplete_expired&#x60;. Paddle: &#x60;active&#x60;, &#x60;trialing&#x60;, &#x60;past_due&#x60;, &#x60;paused&#x60; or &#x60;canceled&#x60;. |  |
| **interval** | **String** |  |  |
| **interval_count** | **Integer** | Number of intervals between payments. |  |
| **quantity** | **Integer** | Units subscribed, multiplying the policy&#39;s machines. |  |
| **price** | [**Price**](Price.md) | Price of one unit for one period, before taxes. |  |
| **current_period_end** | **Time** | End of the paid period, when the subscription renews or ends. |  |
| **cancel_at_period_end** | **Boolean** | Whether the subscription ends at the end of the period. |  |
| **ended_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseSubscription.new(
  provider: null,
  external_id: sub_1MowQVLkdIwHu7ix,
  stripe_subscription_id: sub_1MowQVLkdIwHu7ix,
  status: active,
  interval: null,
  interval_count: 1,
  quantity: 1,
  price: null,
  current_period_end: null,
  cancel_at_period_end: null,
  ended_at: null
)
```

