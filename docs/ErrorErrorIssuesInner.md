# LicenseManager::ErrorErrorIssuesInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **path** | [**Array&lt;ErrorErrorIssuesInnerPathInner&gt;**](ErrorErrorIssuesInnerPathInner.md) |  |  |
| **message** | **String** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ErrorErrorIssuesInner.new(
  path: [name],
  message: Too small: expected string to have &gt;&#x3D;1 characters
)
```

