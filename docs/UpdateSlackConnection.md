# LicenseManager::UpdateSlackConnection

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **events** | **Array&lt;String&gt;** | Notifications the channel gets. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateSlackConnection.new(
  events: [purchased, canceled]
)
```

