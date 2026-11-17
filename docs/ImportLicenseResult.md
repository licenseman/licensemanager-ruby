# LicenseManager::ImportLicenseResult

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **index** | **Integer** | Position of the license in &#x60;licenses&#x60;, from 0. |  |
| **key** | **String** |  |  |
| **status** | **String** | &#x60;created&#x60;: imported. &#x60;skipped&#x60;: a license of the product already uses the key, like one imported before: it&#39;s left as is. &#x60;failed&#x60;: not imported, see &#x60;error&#x60;. |  |
| **license_id** | **String** | Id of the license created, or of the one using the key. |  |
| **error** | [**ImportLicenseResultError**](ImportLicenseResultError.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ImportLicenseResult.new(
  index: null,
  key: null,
  status: null,
  license_id: null,
  error: null
)
```

