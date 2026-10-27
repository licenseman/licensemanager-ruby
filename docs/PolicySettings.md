# LicenseManager::PolicySettings

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **duration** | [**PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional] |
| **max_machines** | **Integer** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional] |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional] |
| **max_version** | [**PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional] |
| **money_back_guarantee_days** | **Integer** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;, which refunds their Stripe payment. Each license keeps the end of its own period as &#x60;cancellableUntil&#x60;. &#x60;null&#x60; for no money back guarantee. Defaults to &#x60;null&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PolicySettings.new(
  duration: null,
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  max_version: null,
  money_back_guarantee_days: 30
)
```

