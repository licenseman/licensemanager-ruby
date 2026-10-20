# LicenseManager::PolicyMaxVersion

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  |  |
| **version** | **String** | &#x60;\&quot;2\&quot;&#x60; allows every 2.y.z version: the minor versions and bug fixes of version 2. &#x60;\&quot;2.3\&quot;&#x60; allows every 2.3.z version: the bug fixes of version 2.3. Bug fixes can&#39;t be locked, so patch numbers like &#x60;\&quot;2.3.1\&quot;&#x60; are rejected. |  |
| **major_after** | [**LockMaxVersionMajorAfter**](LockMaxVersionMajorAfter.md) |  |  |
| **minor_after** | [**LockMaxVersionMinorAfter**](LockMaxVersionMinorAfter.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PolicyMaxVersion.new(
  type: null,
  version: 2.3,
  major_after: null,
  minor_after: null
)
```

