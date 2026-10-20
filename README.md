# LicenseManager Ruby SDK

[![Gem version](https://img.shields.io/gem/v/license_manager)](https://rubygems.org/gems/license_manager)
[![Gem downloads](https://img.shields.io/gem/dt/license_manager)](https://rubygems.org/gems/license_manager)
[![License](https://img.shields.io/github/license/licenseman/licensemanager-ruby)](https://github.com/licenseman/licensemanager-ruby/blob/main/LICENSE)
[![Documentation](https://img.shields.io/badge/docs-licensemanager.dev-blue)](https://licensemanager.dev/docs/sdks/ruby)

The official Ruby SDK for the [LicenseManager](https://licensemanager.dev) API: issue, manage and validate software licenses. Ruby client built on Faraday.

**[Documentation](https://licensemanager.dev/docs/sdks/ruby)** · **[API reference](https://api.licensemanager.dev/docs)** · **[Changelog](CHANGELOG.md)**

## Requirements

Ruby 3.1 or later.

## Installation

```ruby
# Gemfile
gem "license_manager"
```

## Usage

Create an API key in the LicenseManager app, then create a license after a sale:

```ruby
require "license_manager"

LicenseManager.configure do |config|
  config.api_key["x-api-key"] = ENV.fetch("LICENSEMANAGER_API_KEY")
end

licenses = LicenseManager::LicensesApi.new
license = licenses.create_license("x7Kp2QaZ", LicenseManager::CreateLicense.new(email: "jane@example.com"))
```

And validate it from your application, which needs no API key:

```ruby
require "license_manager"

licenses = LicenseManager::LicensesApi.new
license_token = licenses.validate_key("x7Kp2QaZ", LicenseManager::ValidateKey.new(key: "7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF", fingerprint: "4c:32:75:8f:9a:1e", version: "1.4.2"))
```

## Authentication

Most endpoints take an organization API key: keep it on your servers. The endpoints your application calls directly, like validating a key, take no credentials or a token scoped to a customer, license or machine. See [authentication](https://licensemanager.dev/docs/api/authentication) and [scoped tokens](https://licensemanager.dev/docs/api/scoped-tokens).

```ruby
LicenseManager.configure do |config|
  # With an API key, from your backend:
  config.api_key["x-api-key"] = ENV.fetch("LICENSEMANAGER_API_KEY")
  # Or with a token scoped to a customer, license or machine:
  config.access_token = token
end
```

## Errors

Failed requests answer an error with a stable `code` to branch on, listed for each endpoint in the [API reference](https://api.licensemanager.dev/docs). See [errors](https://licensemanager.dev/docs/api/errors).

```ruby
begin
  licenses.get_license("l3Nv8KwB")
rescue LicenseManager::ApiError => error
  # The body is { "error": { "code", "message" } }.
  puts error.code, error.response_body
end
```

## Reference

Every method is documented, with its parameters and responses, in the [`docs`](docs) folder:

| Class | Methods |
| --- | --- |
| [`LicensesApi`](docs/LicensesApi.md) | `validate_key`, `list_licenses`, `create_license`, `list_customer_licenses`, `get_license`, `delete_license`, `update_license`, `get_license_stats`, `send_license_keys`, `get_signing_key` |
| [`PortalApi`](docs/PortalApi.md) | `get_portal`, `request_portal_link`, `create_portal_link`, `send_portal_link` |
| [`ProductsApi`](docs/ProductsApi.md) | `list_products`, `create_product`, `get_product`, `delete_product`, `update_product`, `reset_product`, `upload_product_logo`, `delete_product_logo`, `get_product_stats` |
| [`PoliciesApi`](docs/PoliciesApi.md) | `list_policies`, `create_policy`, `get_policy`, `delete_policy`, `update_policy` |
| [`CustomersApi`](docs/CustomersApi.md) | `list_customers`, `create_customer`, `get_customer`, `delete_customer`, `update_customer` |
| [`MachinesApi`](docs/MachinesApi.md) | `list_machines`, `get_machine`, `deactivate_machine` |
| [`ReleasesApi`](docs/ReleasesApi.md) | `list_releases`, `create_release`, `get_release`, `delete_release`, `update_release` |
| [`TokensApi`](docs/TokensApi.md) | `create_customer_token`, `create_license_token`, `create_machine_token` |
| [`EventsApi`](docs/EventsApi.md) | `list_policy_events`, `list_license_events` |
| [`IntegrationsApi`](docs/IntegrationsApi.md) | `get_stripe_integration`, `connect_stripe`, `disconnect_integration`, `check_integration`, `list_stripe_prices`, `create_stripe_mapping`, `delete_stripe_mapping`, `update_stripe_mapping` |

## Versioning

This SDK follows [semantic versioning](https://semver.org) and is generated from the [OpenAPI document](openapi.json) of the API: each release is listed in the [changelog](CHANGELOG.md). Please don't open pull requests, they would be overwritten by the next release: [open an issue](https://github.com/licenseman/licensemanager-ruby/issues) instead.

## License

See [LICENSE](LICENSE).
