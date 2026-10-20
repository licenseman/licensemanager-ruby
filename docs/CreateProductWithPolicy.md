# LicenseManager::CreateProductWithPolicy

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  |  |
| **slug** | **String** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] |
| **default_policy** | [**PolicySettings**](PolicySettings.md) |  | [optional] |
| **is_test_from_product_id** | **String** | Creates a test product: a sandbox of this live product of the organization, starting with copies of its policies, releases and portal settings. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreateProductWithPolicy.new(
  name: Acme Pro,
  slug: acme-pro,
  default_policy: null,
  is_test_from_product_id: x7Kp2QaZ
)
```

