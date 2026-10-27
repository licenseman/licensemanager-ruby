# LicenseManager::License

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **policy_id** | **String** |  |  |
| **customer_id** | **String** |  |  |
| **key** | **String** | Unique within the product. Case sensitive: &#x60;validateKey&#x60; compares keys exactly. |  |
| **created_at** | **Time** |  |  |
| **expires_at** | **Time** | &#x60;null&#x60; when the license never expires. |  |
| **meta** | **Hash&lt;String, Object&gt;** | Free-form JSON object. |  |
| **stripe_payment_intent_id** | **String** | Id of the Stripe payment intent that paid the license, when it was bought through the Stripe integration. &#x60;null&#x60; otherwise, or when nothing was paid. |  |
| **max_machines** | **Integer** | Maximum number of active machines the license can be used on. &#x60;null&#x60; when there&#39;s no limit. Can be lower than &#x60;activeMachineCount&#x60; after it was lowered: machines aren&#39;t deactivated to match it. |  |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the license: the license tokens returned by &#x60;validateKey&#x60; expire this long after they&#39;re issued, unless the license expires sooner. |  |
| **active_machine_count** | **Integer** | Number of active machines the license is used on. |  |
| **last_activated_at** | **Time** | Last time a machine validated the license key. &#x60;null&#x60; when it was never validated. |  |
| **max_version** | [**LicenseMaxVersion**](LicenseMaxVersion.md) |  |  |
| **price** | [**Price**](Price.md) |  |  |
| **status** | [**LicenseStatus**](LicenseStatus.md) |  |  |
| **cancellable_until** | **Time** | End of the money back guarantee: until then, the customer can cancel the license from the customer portal, or with a token. Set from the policy&#39;s &#x60;moneyBackGuaranteeDays&#x60; when the license is created. &#x60;null&#x60; when the customer can&#39;t cancel it. |  |
| **canceled_at** | **Time** | When the license was canceled: validating its key fails since. &#x60;null&#x60; when it wasn&#39;t. |  |
| **cancellation_reason** | [**CancellationReason**](CancellationReason.md) |  |  |
| **cancellation_comment** | **String** | Comment given when the license was canceled. &#x60;null&#x60; when there&#39;s none. |  |
| **stripe_refund_id** | **String** | Id of the Stripe refund of the license&#39;s payment once it was canceled, through the Stripe integration. &#x60;null&#x60; otherwise. |  |
| **updated_at** | **Time** | Last time the license&#39;s settings were edited, not when its key was validated. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::License.new(
  id: l3Nv8KwB,
  product_id: x7Kp2QaZ,
  policy_id: p4Rt8LmQ,
  customer_id: c9Wd3RtE,
  key: 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  created_at: 2026-01-15T09:30:00.000Z,
  expires_at: 2027-01-15T09:30:00.000Z,
  meta: {seats&#x3D;5},
  stripe_payment_intent_id: pi_3MtwBwLkdIwHu7ix28a3tqPa,
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  active_machine_count: 2,
  last_activated_at: 2026-03-02T14:05:00.000Z,
  max_version: null,
  price: null,
  status: null,
  cancellable_until: 2026-02-14T09:30:00.000Z,
  canceled_at: 2026-01-20T16:12:00.000Z,
  cancellation_reason: null,
  cancellation_comment: I only needed it for one project.,
  stripe_refund_id: re_3MtwBwLkdIwHu7ix0Bs5rA2b,
  updated_at: 2026-01-15T09:30:00.000Z
)
```

