# LicenseManager::Product

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **slug** | **String** |  |  |
| **name** | **String** |  |  |
| **is_test_from_product_id** | **String** | For test products, id of the live product they&#39;re a sandbox of. &#x60;null&#x60; for live products. |  |
| **logo_url** | **String** | Public URL of the product&#39;s logo, shown in the web app and the customer portal. &#x60;null&#x60; without a logo. |  |
| **portal** | [**PortalSettings**](PortalSettings.md) |  |  |
| **auto_machine_change** | **Boolean** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. |  |
| **created_at** | **Time** |  |  |
| **updated_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Product.new(
  id: x7Kp2QaZ,
  slug: acme-pro,
  name: Acme Pro,
  is_test_from_product_id: null,
  logo_url: https://cdn.example.com/logos/x7Kp2QaZ/k3f9a2LpQ7xw.webp,
  portal: null,
  auto_machine_change: true,
  created_at: 2026-01-15T09:30:00.000Z,
  updated_at: 2026-01-15T09:30:00.000Z
)
```

