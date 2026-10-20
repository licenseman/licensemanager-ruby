# LicenseManager::SigningKey

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** | Id of the key, in the &#x60;kid&#x60; header of the tokens it signs. |  |
| **algorithm** | **String** | JWT algorithm of the tokens it signs, with an Ed25519 key. |  |
| **public_key** | **String** | PEM encoded SPKI public key. |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::SigningKey.new(
  id: k8R2vNqW,
  algorithm: null,
  public_key: -----BEGIN PUBLIC KEY-----
MCowBQYDK2VwAyEA…
-----END PUBLIC KEY-----
,
  created_at: 2026-01-15T09:30:00.000Z
)
```

