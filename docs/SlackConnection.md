# LicenseManager::SlackConnection

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **team_id** | **String** |  |  |
| **team_name** | **String** |  |  |
| **channel_id** | **String** |  |  |
| **channel_name** | **String** | Name of the channel when it was connected, with its &#x60;#&#x60;. |  |
| **configuration_url** | **String** | Page of the installation in Slack. |  |
| **events** | **Array&lt;String&gt;** | Notifications the channel gets: &#x60;purchased&#x60; (a license bought through Stripe), &#x60;renewed&#x60; (a subscription renewal paid), &#x60;payment_failed&#x60; (a subscription payment failed) and &#x60;canceled&#x60; (a license canceled, or its subscription ended). |  |
| **status** | **String** | &#x60;revoked&#x60; once Slack refuses the messages, like when the app was removed from the workspace or the channel deleted: remove it and add it again. |  |
| **status_reason** | **String** |  |  |
| **last_sent_at** | **Time** |  |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::SlackConnection.new(
  id: s4Hq8ZpLm,
  team_id: T0123ABCD,
  team_name: Acme,
  channel_id: C0456EFGH,
  channel_name: #sales,
  configuration_url: null,
  events: null,
  status: null,
  status_reason: null,
  last_sent_at: null,
  created_at: null
)
```

