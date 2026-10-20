# LicenseManager::PortalNotFound

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **error** | [**ErrorError**](ErrorError.md) |  |  |
| **organization_slug** | **String** | Slug of the product&#39;s organization. Present on &#x60;portal_disabled&#x60; errors. | [optional] |
| **product_slug** | **String** | Slug of the product. Present on &#x60;portal_disabled&#x60; errors. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PortalNotFound.new(
  error: null,
  organization_slug: acme,
  product_slug: acme-pro
)
```

