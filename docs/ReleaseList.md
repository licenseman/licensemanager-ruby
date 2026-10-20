# LicenseManager::ReleaseList

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **data** | [**Array&lt;Release&gt;**](Release.md) | Items of the page, in the requested order. Empty past the last page. |  |
| **pagination** | [**Pagination**](Pagination.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ReleaseList.new(
  data: null,
  pagination: null
)
```

