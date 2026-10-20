# LicenseManager::UpdateLicense

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **expires_at** | **Time** | &#x60;null&#x60; makes the license never expire. | [optional] |
| **meta** | **Hash&lt;String, Object&gt;** | Free-form JSON object. | [optional] |
| **max_machines** | **Integer** | Maximum number of active machines the license can be used on. &#x60;null&#x60; for no limit. | [optional] |
| **max_offline_duration_seconds** | **Integer** | Longest the applications can run offline with the license, in seconds. At least one hour (&#x60;3600&#x60;). | [optional] |
| **max_version** | [**LicenseMaxVersionInput**](LicenseMaxVersionInput.md) | Latest version of the product the license can use. The values left out are kept. | [optional] |
| **price** | [**PriceInput**](PriceInput.md) |  | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateLicense.new(
  expires_at: 2027-01-15T09:30:00.000Z,
  meta: {seats&#x3D;5},
  max_machines: 3,
  max_offline_duration_seconds: 604800,
  max_version: null,
  price: null
)
```

