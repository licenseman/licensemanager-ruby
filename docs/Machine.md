# LicenseManager::Machine

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **license_id** | **String** |  |  |
| **fingerprint** | **String** | Identifies the machine. Unique within the license. |  |
| **platform** | **String** |  |  |
| **name** | **String** |  |  |
| **status** | **String** | Whether the machine counts as using the license. |  |
| **version** | **String** | Version of the application last validated on the machine. |  |
| **last_validated_at** | **Time** | When the license was last validated on the machine. |  |
| **created_at** | **Time** |  |  |
| **updated_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Machine.new(
  id: m9Tq3VhD,
  license_id: l3Nv8KwB,
  fingerprint: 4c:32:75:8f:9a:1e,
  platform: macOS,
  name: Jane&#39;s MacBook,
  status: active,
  version: 1.4.2,
  last_validated_at: 2026-01-15T09:30:00.000Z,
  created_at: 2026-01-15T09:30:00.000Z,
  updated_at: 2026-01-15T09:30:00.000Z
)
```

