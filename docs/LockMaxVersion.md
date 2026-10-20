# LicenseManager::LockMaxVersion

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  |  |
| **major_after** | [**LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  |  |
| **minor_after** | [**LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LockMaxVersion.new(
  type: null,
  major_after: null,
  minor_after: null
)
```

