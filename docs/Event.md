# LicenseManager::Event

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **type** | [**EventType**](EventType.md) |  |  |
| **created_at** | **Time** |  |  |
| **payload** | **Hash&lt;String, Object&gt;** | Details of the event, depending on its &#x60;type&#x60;. |  |
| **policy_id** | **String** |  |  |
| **license_id** | **String** |  |  |
| **machine_id** | **String** |  |  |
| **machine** | [**EventMachine**](EventMachine.md) |  |  |
| **actor** | [**EventActor**](EventActor.md) |  |  |
| **country** | **String** | ISO 3166-1 alpha-2 code of the country of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
| **latitude** | **Float** | Approximate latitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
| **longitude** | **Float** | Approximate longitude of the IP address the request came from, for &#x60;license.validated&#x60; and &#x60;license.validation_failed&#x60; events. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Event.new(
  id: e6Pw2JcXa,
  type: null,
  created_at: 2026-01-15T09:30:00.000Z,
  payload: {fingerprint&#x3D;4c:32:75:8f:9a:1e, version&#x3D;1.4.2},
  policy_id: null,
  license_id: l3Nv8KwB,
  machine_id: m9Tq3VhD,
  machine: null,
  actor: null,
  country: FR,
  latitude: 48.8566,
  longitude: 2.3522
)
```

