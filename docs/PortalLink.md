# LicenseManager::PortalLink

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **url** | **String** | Link to the customer portal, holding the token. |  |
| **token** | **String** | Customer token in the link, with the &#x60;customer:read&#x60;, &#x60;license:read&#x60;, &#x60;license:cancel&#x60; and &#x60;machine:write&#x60; permissions. |  |
| **expires_at** | **Time** | When the link stops working. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::PortalLink.new(
  url: https://app.licensemanager.dev/portal/x7Kp2QaZ?token&#x3D;eyJhbGciOi…,
  token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…,
  expires_at: 2026-01-22T09:30:00.000Z
)
```

