# LicenseManager::Machine

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **license_id** | **String** |  |  |
| **fingerprint** | **String** | Identifies the machine. Unique within the license. |  |
| **platform** | **String** |  |  |
| **name** | **String** |  |  |
| **status** | **String** | Whether the machine counts as using the license. A &#x60;locked&#x60; machine doesn&#39;t, and its validations are refused with &#x60;machine_locked&#x60;: it overrode a machine that came back. See &#x60;validateKey&#x60;. |  |
| **version** | **String** | Version of the application last validated on the machine. |  |
| **overridden_by_machine_id** | **String** | For a machine deactivated or locked by automatic machine changes, the machine that took its place. Validating the key on a deactivated machine that has one takes its place back. &#x60;null&#x60; otherwise. |  |
| **last_validated_at** | **Time** | When the license was last validated on the machine. |  |
| **country** | **String** | ISO 3166-1 alpha-2 code of the country of the IP address the license was last successfully validated from on the machine. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
| **latitude** | **Float** | Approximate latitude of the IP address the license was last successfully validated from on the machine. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
| **longitude** | **Float** | Approximate longitude of the IP address the license was last successfully validated from on the machine. &#x60;null&#x60; until it&#39;s looked up, shortly after, or when it can&#39;t be. |  |
| **created_at** | **Time** |  |  |
| **updated_at** | **Time** |  |  |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::Machine.new(
  id: m9Tq3VhD,
  license_id: l3Nv8KwB,
  fingerprint: 4c:32:75:8f:9a:1e,
  platform: macOS,
  name: Jane&#39;s MacBook,
  status: active,
  version: 1.4.2,
  overridden_by_machine_id: null,
  last_validated_at: 2026-01-15T09:30:00.000Z,
  country: FR,
  latitude: 48.8566,
  longitude: 2.3522,
  created_at: 2026-01-15T09:30:00.000Z,
  updated_at: 2026-01-15T09:30:00.000Z
)
```

