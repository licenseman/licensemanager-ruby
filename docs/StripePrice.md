# LicenseManager::StripePrice

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **product_name** | **String** |  |  |
| **nickname** | **String** |  |  |
| **price** | [**Price**](Price.md) |  |  |
| **mapped** | **Boolean** | Whether the price already creates licenses of a product. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::StripePrice.new(
  id: price_1MoBy5LkdIwHu7ix,
  product_id: prod_NWjs8kKbJWmuuc,
  product_name: Acme Pro,
  nickname: Launch price,
  price: null,
  mapped: null
)
```

