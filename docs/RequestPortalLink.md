# LicenseManager::RequestPortalLink

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **email** | **String** | Email of the customer. |  |
| **return_url** | **String** | Link back to your website, kept in the emailed link when its domain is one of the product&#39;s &#x60;returnDomains&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::RequestPortalLink.new(
  email: jane@example.com,
  return_url: https://example.com/account
)
```

