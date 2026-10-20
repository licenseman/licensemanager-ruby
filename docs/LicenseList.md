# LicenseManager::LicenseList

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **data** | [**Array&lt;License&gt;**](License.md) | Items of the page, in the requested order. Empty past the last page. |  |
| **pagination** | [**Pagination**](Pagination.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::LicenseList.new(
  data: null,
  pagination: null
)
```

