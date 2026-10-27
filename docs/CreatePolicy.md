# LicenseManager::CreatePolicy

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  |  |
| **slug** | **String** | Unique within the product. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] |
| **is_default** | **Boolean** | &#x60;true&#x60; makes this policy the product&#39;s default, in place of the current one. | [optional] |
| **duration** | [**PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional] |
| **max_machines** | **Integer** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional] |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional] |
| **max_version** | [**PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional] |
| **money_back_guarantee_days** | **Integer** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;, which refunds their Stripe payment. Each license keeps the end of its own period as &#x60;cancellableUntil&#x60;. &#x60;null&#x60; for no money back guarantee. Defaults to &#x60;null&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreatePolicy.new(
  name: Yearly,
  slug: yearly,
  is_default: false,
  duration: null,
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  max_version: null,
  money_back_guarantee_days: 30
)
```

