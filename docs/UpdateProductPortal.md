# LicenseManager::UpdateProductPortal

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **enabled** | **Boolean** | Whether customers can use the customer portal. When disabled, it answers &#x60;404&#x60;. | [optional] |
| **brand_color** | **String** | Background of the portal&#39;s side panel, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | [optional] |
| **accent_color** | **String** | Color of the portal&#39;s inputs and buttons, as &#x60;#rrggbb&#x60;, stored lower cased. &#x60;null&#x60; for the default color. | [optional] |
| **return_url** | **String** | Link back to your website shown in the portal, when the portal&#39;s URL has no allowed &#x60;return_url&#x60;. &#x60;null&#x60; for no link. | [optional] |
| **return_domains** | **Array&lt;String&gt;** | Domains the portal&#39;s &#x60;return_url&#x60; query parameter may point to, their subdomains included. Other return URLs are ignored, in favor of &#x60;returnUrl&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateProductPortal.new(
  enabled: true,
  brand_color: #1e3a8a,
  accent_color: #2563eb,
  return_url: https://example.com/account,
  return_domains: [example.com]
)
```

