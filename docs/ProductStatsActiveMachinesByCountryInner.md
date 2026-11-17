# LicenseManager::ProductStatsActiveMachinesByCountryInner

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **country** | **String** | ISO 3166-1 alpha-2 code of the country the machine was last successfully validated from. &#x60;null&#x60; for the machines it couldn&#39;t be located for. |  |
| **count** | **Integer** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::ProductStatsActiveMachinesByCountryInner.new(
  country: FR,
  count: 42
)
```

