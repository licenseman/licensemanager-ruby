# LicenseManager::Release

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **version** | **String** |  |  |
| **released_at** | **Time** |  |  |
| **created_at** | **Time** |  |  |
| **active_machine_count** | **Integer** | Number of active machines of the product&#39;s licenses running this version: the ones whose &#x60;version&#x60; is exactly the release&#39;s, so &#x60;v2.3.1&#x60; doesn&#39;t count for &#x60;2.3.1&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Release.new(
  id: r4Lm8VwX,
  product_id: x7Kp2QaZ,
  version: 2.3.1,
  released_at: 2026-03-01T12:00:00.000Z,
  created_at: 2026-03-01T12:00:00.000Z,
  active_machine_count: 12
)
```

