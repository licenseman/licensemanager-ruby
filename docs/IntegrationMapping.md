# LicenseManager::IntegrationMapping

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **integration_id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **policy_id** | **String** |  |  |
| **stripe_product_id** | **String** |  |  |
| **stripe_price_id** | **String** |  |  |
| **product_name** | **String** | Name of the Stripe product when it was mapped. |  |
| **price** | [**Price**](Price.md) |  |  |
| **status** | **String** | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |  |
| **status_reason** | **String** |  |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::IntegrationMapping.new(
  id: g2Lk7RwPa,
  integration_id: i8Fz4QnRt,
  product_id: x7Kp2QaZ,
  policy_id: p4Rt8LmQ,
  stripe_product_id: prod_NWjs8kKbJWmuuc,
  stripe_price_id: price_1MoBy5LkdIwHu7ix,
  product_name: Acme Pro,
  price: null,
  status: null,
  status_reason: The price is archived in Stripe,
  created_at: null
)
```

