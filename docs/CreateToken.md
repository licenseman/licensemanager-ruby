# LicenseManager::CreateToken

## Properties

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **scope** | **Array&lt;String&gt;** | Permissions of the token. A write permission implies the matching read one. A token creating a token can only give the permissions it has. |  |
| **expires_in_seconds** | **Integer** | How long the token works, in seconds, from 60 (1 minute) to 31536000 (365 days). Defaults to 900 (15 minutes). A token creating a token can&#39;t give it a later expiration than its own: it&#39;s shortened to it. | [optional][default to 900] |

## Example

```ruby
require 'license_manager'

instance = LicenseManager::CreateToken.new(
  scope: [license:read, machine:write],
  expires_in_seconds: 3600
)
```

