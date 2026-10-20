# LicenseManager::ErrorError

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** |  |  |
| **message** | **String** |  |  |
| **issues** | [**Array&lt;ErrorErrorIssuesInner&gt;**](ErrorErrorIssuesInner.md) | Present on &#x60;validation_error&#x60; errors. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ErrorError.new(
  code: not_found,
  message: Resource not found,
  issues: null
)
```

