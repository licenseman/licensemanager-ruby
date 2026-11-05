# LicenseManager::SlackIntegration

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **configured** | **Boolean** | Whether the server has a Slack app to connect channels with: &#x60;SLACK_CLIENT_ID&#x60; and &#x60;SLACK_CLIENT_SECRET&#x60; are set. |  |
| **connections** | [**Array&lt;SlackConnection&gt;**](SlackConnection.md) | Slack channels getting the product&#39;s notifications. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::SlackIntegration.new(
  configured: null,
  connections: null
)
```

