# LicenseManager::Token

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **token** | **String** | Token to send as &#x60;Authorization: Bearer &lt;token&gt;&#x60;. |  |
| **type** | **String** | Type of resource the token is scoped to. |  |
| **scope** | **Array&lt;String&gt;** |  |  |
| **expires_at** | **Time** | When the token stops working. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Token.new(
  token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…,
  type: license,
  scope: [license:read, machine:write],
  expires_at: 2026-01-15T10:30:00.000Z
)
```

