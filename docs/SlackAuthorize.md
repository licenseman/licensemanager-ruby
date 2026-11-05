# LicenseManager::SlackAuthorize

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **url** | **String** | Slack&#39;s consent screen: open it in the browser to pick the channel. Valid 10 minutes. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::SlackAuthorize.new(
  url: https://slack.com/oauth/v2/authorize?client_id&#x3D;…
)
```

