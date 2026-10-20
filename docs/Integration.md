# LicenseManager::Integration

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **provider** | **String** |  |  |
| **livemode** | **Boolean** | Whether it&#39;s connected in live mode, for the live products, or in test mode, for the test products. |  |
| **account_name** | **String** | Name of the Stripe account, &#x60;null&#x60; when the API key can&#39;t read it. |  |
| **api_key_hint** | **String** | Start and end of the API key, to recognize it. |  |
| **webhook_url** | **String** | URL of the webhook endpoint created on the Stripe account. |  |
| **status** | [**IntegrationStatus**](IntegrationStatus.md) |  |  |
| **status_reason** | **String** | Why the integration isn&#39;t &#x60;active&#x60;, &#x60;null&#x60; when it is. |  |
| **last_checked_at** | **Time** | Last time its health was checked, done every day. |  |
| **last_event_at** | **Time** | Last time it received an event from the provider. |  |
| **created_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Integration.new(
  id: i8Fz4QnRt,
  provider: null,
  livemode: null,
  account_name: Acme Inc.,
  api_key_hint: rk_live_…Ab3d,
  webhook_url: https://api.example.com/v1/webhooks/stripe/i8Fz4QnRt,
  status: null,
  status_reason: The API key can&#39;t manage webhook endpoints: give it the Webhook Endpoints: Write permission,
  last_checked_at: null,
  last_event_at: null,
  created_at: null
)
```

