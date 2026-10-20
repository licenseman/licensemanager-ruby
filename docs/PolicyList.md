# LicenseManager::PolicyList

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **data** | [**Array&lt;Policy&gt;**](Policy.md) | Items of the page, in the requested order. Empty past the last page. |  |
| **pagination** | [**Pagination**](Pagination.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PolicyList.new(
  data: null,
  pagination: null
)
```

