# LicenseManager::Pagination

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **page** | **Integer** | Number of the returned page, as requested. Pages are numbered from 1: &#x60;1&#x60; is the first page. |  |
| **page_size** | **Integer** | Maximum number of items per page, as requested. &#x60;data&#x60; holds fewer items on the last page, and none past it. |  |
| **total** | **Integer** | Number of items matching the filters, across all pages. &#x60;0&#x60; when nothing matches. |  |
| **total_pages** | **Integer** | Number of pages, which is also the number of the last page. &#x60;0&#x60; when nothing matches. There&#39;s a next page while &#x60;page&#x60; is lower than &#x60;totalPages&#x60;. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Pagination.new(
  page: 1,
  page_size: 20,
  total: 42,
  total_pages: 3
)
```

