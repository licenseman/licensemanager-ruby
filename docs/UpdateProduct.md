# LicenseManager::UpdateProduct

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **slug** | **String** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] |
| **portal** | [**UpdateProductPortal**](UpdateProductPortal.md) |  | [optional] |
| **auto_machine_change** | **Boolean** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateProduct.new(
  name: Acme Pro,
  slug: acme-pro,
  portal: null,
  auto_machine_change: true
)
```

