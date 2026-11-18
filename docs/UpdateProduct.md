# LicenseManager::UpdateProduct

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **name** | **String** |  | [optional] |
| **slug** | **String** | Unique within the organization. Defaults to the name, lower cased, without accents and special characters. Starts with &#x60;test_&#x60; in test products, which is added when missing, and removed in live products. | [optional] |
| **website_url** | **String** | The product&#39;s website, linked from the customer portal, when its URL has no allowed &#x60;return_url&#x60;, and from the emails sent to customers. &#x60;null&#x60; for no link. | [optional] |
| **download_url** | **String** | Where customers download the product, linked from the email sending their license keys. &#x60;null&#x60; for no link. | [optional] |
| **portal** | [**UpdateProductPortal**](UpdateProductPortal.md) |  | [optional] |
| **auto_machine_change** | **Boolean** | Whether a new machine validating a license already on its max machines takes the place of the license&#39;s machine validated the longest ago, rather than being refused with &#x60;machine_limit_reached&#x60;. When the replaced machine is validated again, it takes its place back and the machine that replaced it is locked. See &#x60;validateKey&#x60;. | [optional] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::UpdateProduct.new(
  name: Acme Pro,
  slug: acme-pro,
  website_url: https://example.com,
  download_url: https://example.com/download,
  portal: null,
  auto_machine_change: true
)
```

