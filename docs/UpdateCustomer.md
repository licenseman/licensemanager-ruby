# LicenseManager::UpdateCustomer

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | Unique within the product, regardless of case. Stored lower cased. | [optional] |
| **name** | **String** | Display name of the customer. &#x60;null&#x60; when unknown. Defaults to &#x60;null&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateCustomer.new(
  email: jane@example.com,
  name: Jane Doe
)
```

