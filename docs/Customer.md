# LicenseManager::Customer

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **product_id** | **String** |  |  |
| **email** | **String** |  |  |
| **name** | **String** | Display name of the customer. &#x60;null&#x60; when unknown. |  |
| **license_count** | **Integer** | Number of licenses of this customer. |  |
| **stripe_customer_id** | **String** | Id of the Stripe customer, when the customer bought licenses through the Stripe integration as a Stripe customer. &#x60;null&#x60; otherwise, e.g. for a guest checkout. |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Customer.new(
  id: c9Wd3RtE,
  product_id: x7Kp2QaZ,
  email: jane@example.com,
  name: Jane Doe,
  license_count: 3,
  stripe_customer_id: cus_NffrFeUfNV2Hib,
  created_at: 2026-01-15T09:30:00.000Z
)
```

