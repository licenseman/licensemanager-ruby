# LicenseManager::LockMaxVersionMajorAfterOneOf1

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **value** | **Integer** |  |  |
| **unit** | **String** | Calendar months: a license created on January 31 with a 1 month duration expires on the last day of February. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LockMaxVersionMajorAfterOneOf1.new(
  value: 12,
  unit: null
)
```

