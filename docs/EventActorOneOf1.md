# LicenseManager::EventActorOneOf1

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **type** | **String** |  |  |
| **id** | **String** | &#x60;null&#x60; when the API key has been deleted. |  |
| **name** | **String** |  |  |
| **start** | **String** | First characters of the key, to recognize it. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::EventActorOneOf1.new(
  type: null,
  id: k5Rt7WmNb,
  name: Billing backend,
  start: lm_Ab3d
)
```

