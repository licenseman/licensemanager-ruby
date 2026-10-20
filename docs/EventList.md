# LicenseManager::EventList

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **data** | [**Array&lt;Event&gt;**](Event.md) | Items of the page, in the requested order. Empty past the last page. |  |
| **pagination** | [**Pagination**](Pagination.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::EventList.new(
  data: null,
  pagination: null
)
```

