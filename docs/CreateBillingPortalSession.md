# LicenseManager::CreateBillingPortalSession

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **return_url** | **String** | Where the Stripe customer portal links back to: a page of the customer portal, or of one of the product&#39;s &#x60;returnDomains&#x60;. The customer portal of the product by default. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreateBillingPortalSession.new(
  return_url: https://example.com/account
)
```

