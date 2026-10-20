# LicenseManager::ValidateKeyErrorError

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **code** | **String** |  |  |
| **message** | **String** |  |  |
| **issues** | [**Array&lt;ErrorErrorIssuesInner&gt;**](ErrorErrorIssuesInner.md) | Present on &#x60;validation_error&#x60; errors. | [optional] |
| **latest_allowed_version** | **String** | On &#x60;version_not_allowed&#x60; errors: version of the latest stable release of the product the license allows, among the ones already released. &#x60;null&#x60; when it allows none of them. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ValidateKeyErrorError.new(
  code: not_found,
  message: Resource not found,
  issues: null,
  latest_allowed_version: 2.3.1
)
```

