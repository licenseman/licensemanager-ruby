# LicenseManager::PolicySettings

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **duration** | [**PolicySettingsDuration**](PolicySettingsDuration.md) |  | [optional] |
| **max_machines** | **Integer** | Maximum number of active machines of the licenses created with this policy, copied to each of them. &#x60;null&#x60; for no limit. Defaults to &#x60;null&#x60;. | [optional] |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds, copied to each of them. At least one hour (&#x60;3600&#x60;). Defaults to one week. | [optional] |
| **max_version** | [**PolicySettingsMaxVersion**](PolicySettingsMaxVersion.md) |  | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PolicySettings.new(
  duration: null,
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  max_version: null
)
```

