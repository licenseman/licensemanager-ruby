# LicenseManager::LicenseCustomer

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **email** | **String** |  |  |
| **name** | **String** | Display name of the customer. &#x60;null&#x60; when unknown. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseCustomer.new(
  id: c9Wd3RtE,
  email: jane@example.com,
  name: Jane Doe
)
```

