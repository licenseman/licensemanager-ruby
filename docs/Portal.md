# LicenseManager::Portal

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **product_name** | **String** |  |  |
| **organization_name** | **String** |  |  |
| **logo_url** | **String** | Public URL of the product&#39;s logo. &#x60;null&#x60; without a logo. |  |
| **brand_color** | **String** | Background of the side panel, as &#x60;#rrggbb&#x60;. &#x60;null&#x60; for the default color. |  |
| **accent_color** | **String** | Color of the inputs and buttons, as &#x60;#rrggbb&#x60;. &#x60;null&#x60; for the default color. |  |
| **return_url** | **String** | Link back to the product&#39;s website: the requested &#x60;returnUrl&#x60; when its domain is allowed, the product&#39;s default return link otherwise. &#x60;null&#x60; for no link. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Portal.new(
  product_id: x7Kp2QaZ,
  product_name: Acme Pro,
  organization_name: Acme,
  logo_url: https://cdn.example.com/logos/x7Kp2QaZ/k3f9a2LpQ7xw.webp,
  brand_color: #1e3a8a,
  accent_color: #2563eb,
  return_url: https://example.com/account
)
```

