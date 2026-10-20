# LicenseManager::CreatePortalLink

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **expires_in_seconds** | **Integer** | How long the link works, in seconds, from 300 (5 minutes) to 31536000 (365 days). |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreatePortalLink.new(
  expires_in_seconds: 604800
)
```

