# LicenseManager::PaddlePrice

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **product_name** | **String** |  |  |
| **description** | **String** | Name or internal description of the price in Paddle. |  |
| **price** | [**Price**](Price.md) |  |  |
| **recurring** | [**StripePriceRecurring**](StripePriceRecurring.md) |  |  |
| **mapped** | **Boolean** | Whether the price already creates licenses of a product. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PaddlePrice.new(
  id: pri_01gsz8x8sawmvhz1pv30nge1ke,
  product_id: pro_01gsz4t5hdjse780zja8vvr7jg,
  product_name: Acme Pro,
  description: Launch price,
  price: null,
  recurring: null,
  mapped: null
)
```

