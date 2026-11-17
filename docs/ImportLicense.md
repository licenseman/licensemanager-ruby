# LicenseManager::ImportLicense

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | Email of the customer the license belongs to. The product&#39;s customer with this email, compared regardless of case, or a new one when there&#39;s none. |  |
| **key** | **String** | The license&#39;s current key, kept as is. Case sensitive. Starts with &#x60;TEST-&#x60; in test products, which is added when missing, and removed in live products. |  |
| **policy_id** | **String** | Policy of the product the license follows. Defaults to the product&#39;s default policy. | [optional] |
| **expires_at** | **Time** | &#x60;null&#x60; makes the license never expire. Defaults to the creation date plus the duration of the policy, or &#x60;null&#x60; when the policy has none. | [optional] |
| **meta** | **Hash&lt;String, Object&gt;** | Free-form JSON object. | [optional] |
| **max_machines** | **Integer** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. Defaults to the one of the policy. | [optional] |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). Defaults to the one of the policy. | [optional] |
| **price** | [**PriceInput**](PriceInput.md) |  | [optional] |
| **max_version** | [**LicenseMaxVersionInput**](LicenseMaxVersionInput.md) |  | [optional] |
| **cancellable_until** | **Time** | End of the money back guarantee: until then, the customer can cancel the license from the customer portal, or with a token. &#x60;null&#x60; to not let them. Defaults to the creation date plus the policy&#39;s &#x60;moneyBackGuaranteeDays&#x60;, or &#x60;null&#x60; when it has none. | [optional] |
| **name** | **String** | Name of the customer, given to it when it has none yet. | [optional] |
| **subscription** | [**ImportLicenseSubscription**](ImportLicenseSubscription.md) |  | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ImportLicense.new(
  email: jane@example.com,
  key: 7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF,
  policy_id: p4Rt8LmQ,
  expires_at: 2027-01-15T09:30:00.000Z,
  meta: {seats&#x3D;5},
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  price: null,
  max_version: null,
  cancellable_until: 2026-02-14T09:30:00.000Z,
  name: Jane Doe,
  subscription: null
)
```

