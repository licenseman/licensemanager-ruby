# LicenseManager::ImportLicensesResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **created** | **Integer** |  |  |
| **skipped** | **Integer** |  |  |
| **failed** | **Integer** |  |  |
| **results** | [**Array&lt;ImportLicenseResult&gt;**](ImportLicenseResult.md) | Result of each license, in the order sent. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ImportLicensesResult.new(
  created: null,
  skipped: null,
  failed: null,
  results: null
)
```

