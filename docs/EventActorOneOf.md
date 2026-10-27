# LicenseManager::EventActorOneOf

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  |  |
| **id** | **String** | &#x60;null&#x60; when the user has been deleted. |  |
| **name** | **String** |  |  |
| **email** | **String** |  |  |
| **image** | **String** | URL of the user&#39;s profile picture. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::EventActorOneOf.new(
  type: null,
  id: u2Hk9PzLq,
  name: Jane Doe,
  email: jane@licensemanager.dev,
  image: https://example.com/jane.png
)
```

