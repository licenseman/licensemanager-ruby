# LicenseManager::IntegrationMapping

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **integration_id** | **String** |  |  |
| **provider** | **String** |  |  |
| **product_id** | **String** |  |  |
| **policy_id** | **String** |  |  |
| **external_product_id** | **String** | Id of the product in the provider: &#x60;prod_…&#x60; in Stripe, &#x60;pro_…&#x60; in Paddle. |  |
| **external_price_id** | **String** | Id of the price in the provider: &#x60;price_…&#x60; in Stripe, &#x60;pri_…&#x60; in Paddle. |  |
| **stripe_product_id** | **String** | Deprecated: use &#x60;externalProductId&#x60;, which it equals. |  |
| **stripe_price_id** | **String** | Deprecated: use &#x60;externalPriceId&#x60;, which it equals. |  |
| **product_name** | **String** | Name of the provider&#39;s product when it was mapped. |  |
| **price** | [**Price**](Price.md) |  |  |
| **recurring** | [**IntegrationMappingRecurring**](IntegrationMappingRecurring.md) |  |  |
| **status** | **String** | &#x60;error&#x60; when the price can no longer be paid, explained by &#x60;statusReason&#x60;. |  |
| **status_reason** | **String** |  |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::IntegrationMapping.new(
  id: g2Lk7RwPa,
  integration_id: i8Fz4QnRt,
  provider: null,
  product_id: x7Kp2QaZ,
  policy_id: p4Rt8LmQ,
  external_product_id: prod_NWjs8kKbJWmuuc,
  external_price_id: price_1MoBy5LkdIwHu7ix,
  stripe_product_id: prod_NWjs8kKbJWmuuc,
  stripe_price_id: price_1MoBy5LkdIwHu7ix,
  product_name: Acme Pro,
  price: null,
  recurring: null,
  status: null,
  status_reason: The price is archived in Stripe,
  created_at: null
)
```

