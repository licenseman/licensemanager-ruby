# LicenseManager::MachineList

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **data** | [**Array&lt;Machine&gt;**](Machine.md) | Items of the page, in the requested order. Empty past the last page. |  |
| **pagination** | [**Pagination**](Pagination.md) |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::MachineList.new(
  data: null,
  pagination: null
)
```

