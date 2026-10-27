# LicenseManager::Policy

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **slug** | **String** |  |  |
| **name** | **String** |  |  |
| **is_default** | **Boolean** | Whether this is the product&#39;s default policy. Each product has exactly one. |  |
| **duration** | [**PolicyDuration**](PolicyDuration.md) |  |  |
| **max_machines** | **Integer** | Maximum number of active machines of the licenses created with this policy. &#x60;null&#x60; when there&#39;s no limit. |  |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the licenses created with this policy, in seconds. |  |
| **max_version** | [**PolicyMaxVersion**](PolicyMaxVersion.md) |  |  |
| **money_back_guarantee_days** | **Integer** | Number of days after their creation during which customers can cancel the licenses created with this policy, from the customer portal or with &#x60;cancelLicense&#x60;. &#x60;null&#x60; when they can&#39;t. |  |
| **license_count** | **Integer** | Number of licenses following this policy. |  |
| **created_at** | **Time** |  |  |
| **updated_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Policy.new(
  id: p4Rt8LmQ,
  product_id: x7Kp2QaZ,
  slug: yearly,
  name: Yearly,
  is_default: false,
  duration: null,
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  max_version: null,
  money_back_guarantee_days: 30,
  license_count: 12,
  created_at: 2026-01-15T09:30:00.000Z,
  updated_at: 2026-01-15T09:30:00.000Z
)
```

