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
  actor: null
)
```

