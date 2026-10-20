# LicenseManager::UpdateRelease

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **version** | **String** | Semantic version, like &#x60;\&quot;2.3.1\&quot;&#x60; or &#x60;\&quot;2.4.0-beta.1\&quot;&#x60;, without a &#x60;v&#x60; prefix. Unique within the product. Each number has at most 9 digits. | [optional] |
| **released_at** | **Time** | When the version is released, which can be in the future. Defaults to now. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateRelease.new(
  version: 2.3.1,
  released_at: 2026-03-01T12:00:00.000Z
)
```

