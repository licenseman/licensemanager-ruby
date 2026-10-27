# LicenseManager::LicensesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**cancel_license**](LicensesApi.md#cancel_license) | **POST** /v1/licenses/{id}/cancel | Cancel a license |
| [**create_license**](LicensesApi.md#create_license) | **POST** /v1/products/{productId}/licenses | Create a license |
| [**delete_license**](LicensesApi.md#delete_license) | **DELETE** /v1/licenses/{id} | Delete a license |
| [**get_license**](LicensesApi.md#get_license) | **GET** /v1/licenses/{id} | Get a license |
| [**get_license_stats**](LicensesApi.md#get_license_stats) | **GET** /v1/licenses/{id}/stats | Get the stats of a license |
| [**get_signing_key**](LicensesApi.md#get_signing_key) | **GET** /v1/signing-key | Get the organization&#39;s signing key |
| [**list_customer_licenses**](LicensesApi.md#list_customer_licenses) | **GET** /v1/customers/{customerId}/licenses | List the licenses of a customer |
| [**list_licenses**](LicensesApi.md#list_licenses) | **GET** /v1/products/{productId}/licenses | List the licenses of a product |
| [**send_license_keys**](LicensesApi.md#send_license_keys) | **POST** /v1/licenses/send-keys | Email license keys to their customers |
| [**update_license**](LicensesApi.md#update_license) | **PATCH** /v1/licenses/{id} | Update a license |
| [**validate_key**](LicensesApi.md#validate_key) | **POST** /v1/products/{productId}/validate-key | Validate a license key |


## cancel_license

> <License> cancel_license(id, cancel_license)

Cancel a license

Cancels the license right away: validating its key then fails with `license_expired`, like an expired license, and its status is `canceled`. A cancellation can't be undone.  Customers can cancel their licenses until their `cancellableUntil`, the end of their money back guarantee: tokens can't cancel a license past it, or without one. API keys and sessions can cancel any license.  When the license was bought through the Stripe integration, its payment is refunded in the background, unless the integration disables `autoRefund`, its API key lacks the optional Refunds: Write permission (`canRefund`), or `refund` is `false`: the refund is its price paid, taxes included, and its id is set as `stripeRefundId`. The customer is emailed a confirmation, and the owners and admins of the organization are told about the cancellation and its refund. In test products, the customer is only emailed when their email is a member's of the organization.  A subscription license isn't refunded: its Stripe subscription is canceled at once, without proration, which needs the integration's `canManageSubscriptions`.  Records a `license.canceled` event, then a `license.refunded` or `license.refund_failed` one once the refund is done.  **Token access**: customer, license tokens with the `license:cancel` permission (or the matching write one). A token reaches the license it's scoped to, or the licenses of its customer.  **Required role permission**: `license:cancel` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'

  # Configure Bearer authorization (JWT): token
  config.access_token = 'YOUR_BEARER_TOKEN'
end

api_instance = LicenseManager::LicensesApi.new
id = 'l3Nv8KwB' # String | 
cancel_license = LicenseManager::CancelLicense.new({reason: LicenseManager::CancellationReason::TOO_EXPENSIVE}) # CancelLicense | 

begin
  # Cancel a license
  result = api_instance.cancel_license(id, cancel_license)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->cancel_license: #{e}"
end
```

#### Using the cancel_license_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<License>, Integer, Hash)> cancel_license_with_http_info(id, cancel_license)

```ruby
begin
  # Cancel a license
  data, status_code, headers = api_instance.cancel_license_with_http_info(id, cancel_license)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <License>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->cancel_license_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **cancel_license** | [**CancelLicense**](CancelLicense.md) |  |  |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## create_license

> <License> create_license(product_id, create_license)

Create a license

Without a `key`, the license gets a random one, like `7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF`: 5 groups of 5 characters separated by dashes, each character an upper case letter or a digit other than `O`, `0`, `I` and `1`. That's 32 possible characters encoding 5 bits each, for 125 random bits.  Without a `policyId`, the license follows the product's default policy.  Without an `expiresAt`, the license expires after the duration of its policy, or never when the policy has none. `expiresAt: null` makes it never expire.  Without a `price`, the price paid for the license is unknown: it's left out of the revenue stats.  Without a `cancellableUntil`, the customer can cancel the license during the policy's `moneyBackGuaranteeDays` after its creation, or never when the policy has none.  The values of `maxVersion` left out are taken from the max version of the policy: its hard-coded version, or the times after the creation of the license its versions lock.  The license belongs to the product's customer with the given `email`, which is created when there's none.  With `sendKey: true`, the key is emailed to the customer once the license is created.  The license copies the settings of its policy when it's created: later changes to the policy don't affect it. Its key, policy and customer can't be changed afterwards.  **Required role permission**: `license:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
product_id = 'x7Kp2QaZ' # String | 
create_license = LicenseManager::CreateLicense.new({email: 'jane@example.com'}) # CreateLicense | 

begin
  # Create a license
  result = api_instance.create_license(product_id, create_license)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->create_license: #{e}"
end
```

#### Using the create_license_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<License>, Integer, Hash)> create_license_with_http_info(product_id, create_license)

```ruby
begin
  # Create a license
  data, status_code, headers = api_instance.create_license_with_http_info(product_id, create_license)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <License>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->create_license_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **create_license** | [**CreateLicense**](CreateLicense.md) |  |  |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_license

> delete_license(id)

Delete a license

Deletes the license along with its deactivated machines. A license used on active machines can't be deleted: deactivate them first. The tokens scoped to the license or its machines stop working, but the license tokens `validateKey` already returned stay valid until they expire. Its events can no longer be listed.  **Required role permission**: `license:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
id = 'l3Nv8KwB' # String | 

begin
  # Delete a license
  api_instance.delete_license(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->delete_license: #{e}"
end
```

#### Using the delete_license_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_license_with_http_info(id)

```ruby
begin
  # Delete a license
  data, status_code, headers = api_instance.delete_license_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->delete_license_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

nil (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_license

> <License> get_license(id)

Get a license

**Token access**: customer, license, machine tokens with the `license:read` permission (or the matching write one). A token reaches the license it's scoped to, the licenses of its customer, or the license of its machine.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'

  # Configure Bearer authorization (JWT): token
  config.access_token = 'YOUR_BEARER_TOKEN'
end

api_instance = LicenseManager::LicensesApi.new
id = 'l3Nv8KwB' # String | 

begin
  # Get a license
  result = api_instance.get_license(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_license: #{e}"
end
```

#### Using the get_license_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<License>, Integer, Hash)> get_license_with_http_info(id)

```ruby
begin
  # Get a license
  data, status_code, headers = api_instance.get_license_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <License>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_license_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_license_stats

> <LicenseStats> get_license_stats(id)

Get the stats of a license

Daily number of successful activations of the license over the last 90 days, today included, per machine and per version of the application. Days are in UTC.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
id = 'l3Nv8KwB' # String | 

begin
  # Get the stats of a license
  result = api_instance.get_license_stats(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_license_stats: #{e}"
end
```

#### Using the get_license_stats_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<LicenseStats>, Integer, Hash)> get_license_stats_with_http_info(id)

```ruby
begin
  # Get the stats of a license
  data, status_code, headers = api_instance.get_license_stats_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <LicenseStats>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_license_stats_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**LicenseStats**](LicenseStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_signing_key

> <SigningKey> get_signing_key

Get the organization's signing key

Public key verifying the license tokens returned by `validateKey`, to embed in applications. Created the first time it's needed, and never rotated. The organization has a single key, signing the tokens of its live and test products alike: check the tokens' `aud` to tell them apart.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new

begin
  # Get the organization's signing key
  result = api_instance.get_signing_key
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_signing_key: #{e}"
end
```

#### Using the get_signing_key_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SigningKey>, Integer, Hash)> get_signing_key_with_http_info

```ruby
begin
  # Get the organization's signing key
  data, status_code, headers = api_instance.get_signing_key_with_http_info
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SigningKey>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->get_signing_key_with_http_info: #{e}"
end
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**SigningKey**](SigningKey.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_customer_licenses

> <LicenseList> list_customer_licenses(customer_id, opts)

List the licenses of a customer

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.  **Token access**: customer tokens with the `license:read` permission (or the matching write one). A customer token reaches its own licenses.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'

  # Configure Bearer authorization (JWT): token
  config.access_token = 'YOUR_BEARER_TOKEN'
end

api_instance = LicenseManager::LicensesApi.new
customer_id = 'c9Wd3RtE' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'key', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  search: 'X9ZPA', # String | Case-insensitive text the key contains.
  key: '7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF', # String | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
  policy_id: 'p4Rt8LmQ', # String | Only returns the licenses following this policy.
  machine_version: '2.3.1', # String | Only returns the licenses with at least one active machine running this version of the product.
  status: LicenseManager::LicenseStatus::ACTIVE, # LicenseStatus | Only returns the licenses with this status.
  created_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses created at or after this date.
  created_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses created at or before this date.
  last_activated_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
  last_activated_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
  never_activated: 'true', # String | `true` only returns the licenses never activated, `false` only the ones activated at least once.
  expires_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
  expires_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
  never_expires: 'true', # String | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
  currency: 'USD', # String | Only returns the licenses paid in this currency.
  price: 49.99, # Float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  price_min: 49.99, # Float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  price_max: 49.99, # Float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  has_price: 'true' # String | `true` only returns the licenses with a price, `false` only the ones without.
}

begin
  # List the licenses of a customer
  result = api_instance.list_customer_licenses(customer_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->list_customer_licenses: #{e}"
end
```

#### Using the list_customer_licenses_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<LicenseList>, Integer, Hash)> list_customer_licenses_with_http_info(customer_id, opts)

```ruby
begin
  # List the licenses of a customer
  data, status_code, headers = api_instance.list_customer_licenses_with_http_info(customer_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <LicenseList>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->list_customer_licenses_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **customer_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **search** | **String** | Case-insensitive text the key contains. | [optional] |
| **key** | **String** | Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policy_id** | **String** | Only returns the licenses following this policy. | [optional] |
| **machine_version** | **String** | Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**LicenseStatus**](.md) | Only returns the licenses with this status. | [optional] |
| **created_from** | **Time** | Only returns the licenses created at or after this date. | [optional] |
| **created_to** | **Time** | Only returns the licenses created at or before this date. | [optional] |
| **last_activated_from** | **Time** | Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **last_activated_to** | **Time** | Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **never_activated** | **String** | &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] |
| **expires_from** | **Time** | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expires_to** | **Time** | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **never_expires** | **String** | &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] |
| **currency** | **String** | Only returns the licenses paid in this currency. | [optional] |
| **price** | **Float** | Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_min** | **Float** | Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_max** | **Float** | Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **has_price** | **String** | &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_licenses

> <LicenseList> list_licenses(product_id, opts)

List the licenses of a product

Sorting by `lastActivatedAt` puts the licenses never activated last in both orders. Sorting by `price` compares the amounts whatever their currency, and puts the licenses without a price last in both orders.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
product_id = 'x7Kp2QaZ' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'key', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  search: 'X9ZPA', # String | Case-insensitive text the key contains.
  key: '7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF', # String | Only returns the license with this exact key, case included. Keys of test products start with `TEST-`.
  policy_id: 'p4Rt8LmQ', # String | Only returns the licenses following this policy.
  customer_id: 'c9Wd3RtE', # String | Only returns the licenses of this customer.
  machine_version: '2.3.1', # String | Only returns the licenses with at least one active machine running this version of the product.
  status: LicenseManager::LicenseStatus::ACTIVE, # LicenseStatus | Only returns the licenses with this status.
  created_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses created at or after this date.
  created_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses created at or before this date.
  last_activated_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses last activated at or after this date. Licenses never activated are left out.
  last_activated_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses last activated at or before this date. Licenses never activated are left out.
  never_activated: 'true', # String | `true` only returns the licenses never activated, `false` only the ones activated at least once.
  expires_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the licenses expiring at or after this date. Licenses that never expire are left out.
  expires_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the licenses expiring at or before this date. Licenses that never expire are left out.
  never_expires: 'true', # String | `true` only returns the licenses that never expire, `false` only the ones with an expiration date.
  currency: 'USD', # String | Only returns the licenses paid in this currency.
  price: 49.99, # Float | Only returns the licenses paid exactly this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  price_min: 49.99, # Float | Only returns the licenses paid at least this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  price_max: 49.99, # Float | Only returns the licenses paid at most this amount, in major units of its currency: combine with `currency` to compare amounts of one currency. Licenses without a price are left out.
  has_price: 'true' # String | `true` only returns the licenses with a price, `false` only the ones without.
}

begin
  # List the licenses of a product
  result = api_instance.list_licenses(product_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->list_licenses: #{e}"
end
```

#### Using the list_licenses_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<LicenseList>, Integer, Hash)> list_licenses_with_http_info(product_id, opts)

```ruby
begin
  # List the licenses of a product
  data, status_code, headers = api_instance.list_licenses_with_http_info(product_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <LicenseList>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->list_licenses_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **search** | **String** | Case-insensitive text the key contains. | [optional] |
| **key** | **String** | Only returns the license with this exact key, case included. Keys of test products start with &#x60;TEST-&#x60;. | [optional] |
| **policy_id** | **String** | Only returns the licenses following this policy. | [optional] |
| **customer_id** | **String** | Only returns the licenses of this customer. | [optional] |
| **machine_version** | **String** | Only returns the licenses with at least one active machine running this version of the product. | [optional] |
| **status** | [**LicenseStatus**](.md) | Only returns the licenses with this status. | [optional] |
| **created_from** | **Time** | Only returns the licenses created at or after this date. | [optional] |
| **created_to** | **Time** | Only returns the licenses created at or before this date. | [optional] |
| **last_activated_from** | **Time** | Only returns the licenses last activated at or after this date. Licenses never activated are left out. | [optional] |
| **last_activated_to** | **Time** | Only returns the licenses last activated at or before this date. Licenses never activated are left out. | [optional] |
| **never_activated** | **String** | &#x60;true&#x60; only returns the licenses never activated, &#x60;false&#x60; only the ones activated at least once. | [optional] |
| **expires_from** | **Time** | Only returns the licenses expiring at or after this date. Licenses that never expire are left out. | [optional] |
| **expires_to** | **Time** | Only returns the licenses expiring at or before this date. Licenses that never expire are left out. | [optional] |
| **never_expires** | **String** | &#x60;true&#x60; only returns the licenses that never expire, &#x60;false&#x60; only the ones with an expiration date. | [optional] |
| **currency** | **String** | Only returns the licenses paid in this currency. | [optional] |
| **price** | **Float** | Only returns the licenses paid exactly this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_min** | **Float** | Only returns the licenses paid at least this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **price_max** | **Float** | Only returns the licenses paid at most this amount, in major units of its currency: combine with &#x60;currency&#x60; to compare amounts of one currency. Licenses without a price are left out. | [optional] |
| **has_price** | **String** | &#x60;true&#x60; only returns the licenses with a price, &#x60;false&#x60; only the ones without. | [optional] |

### Return type

[**LicenseList**](LicenseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## send_license_keys

> send_license_keys(send_license_keys)

Email license keys to their customers

Emails each customer the keys of its licenses among `ids`, with their expiration date: one email per customer, whatever their number of licenses. The licenses can belong to different products of the organization.  Test products only email the members of the organization, so testing never emails real customers: nothing is sent when a license of a test product belongs to a customer whose email isn't a member's.  **Required role permission**: `license:send` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
send_license_keys = LicenseManager::SendLicenseKeys.new({ids: [l3Nv8KwB]}) # SendLicenseKeys | 

begin
  # Email license keys to their customers
  api_instance.send_license_keys(send_license_keys)
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->send_license_keys: #{e}"
end
```

#### Using the send_license_keys_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> send_license_keys_with_http_info(send_license_keys)

```ruby
begin
  # Email license keys to their customers
  data, status_code, headers = api_instance.send_license_keys_with_http_info(send_license_keys)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->send_license_keys_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **send_license_keys** | [**SendLicenseKeys**](SendLicenseKeys.md) |  |  |

### Return type

nil (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## update_license

> <License> update_license(id, update_license)

Update a license

The key, policy and customer of a license can't be changed: sending them does nothing.  The changes apply to the next validations of the key, not to the license tokens `validateKey` already returned, which stay valid until they expire. Lowering `maxMachines` doesn't deactivate machines: the ones already active keep validating, and new ones replace them one at a time when the product has `autoMachineChange`, or are refused until enough are deactivated.  **Required role permission**: `license:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

### Examples

```ruby
require 'time'
require 'license_manager'
# setup authorization
LicenseManager.configure do |config|
  # Configure API key authorization: apiKey
  config.api_key['x-api-key'] = 'YOUR API KEY'
  # Uncomment the following line to set a prefix for the API key, e.g. 'Bearer' (defaults to nil)
  # config.api_key_prefix['x-api-key'] = 'Bearer'
end

api_instance = LicenseManager::LicensesApi.new
id = 'l3Nv8KwB' # String | 
update_license = LicenseManager::UpdateLicense.new # UpdateLicense | 

begin
  # Update a license
  result = api_instance.update_license(id, update_license)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->update_license: #{e}"
end
```

#### Using the update_license_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<License>, Integer, Hash)> update_license_with_http_info(id, update_license)

```ruby
begin
  # Update a license
  data, status_code, headers = api_instance.update_license_with_http_info(id, update_license)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <License>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->update_license_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_license** | [**UpdateLicense**](UpdateLicense.md) |  |  |

### Return type

[**License**](License.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## validate_key

> <LicenseToken> validate_key(product_id, validate_key)

Validate a license key

Checks the license key of the product on a machine and returns a token the application can verify offline with the organization's public key. Doesn't need authentication.  The license must allow the `version`: up to its `maxVersion.version` when it has one, like `\"2.3\"` for every 2.3.z version and older. Its `maxVersion.lockMajorAt` and `maxVersion.lockMinorAt` are enforced once they hard-code `maxVersion.version`, within the hour they're reached. When it doesn't, the error's `latestAllowedVersion` is the latest release of the product the license allows, so the application can offer to install it.  The machine with the `fingerprint` is created when the license has none, and activated when it's deactivated, unless the license is already active on its maximum number of machines. A machine that's already active is never refused for the maximum number of machines, even when it was lowered below the number of active machines. Its `version`, and its `name` and `platform` when given, are updated: they can't be cleared.  Unless the product disables `autoMachineChange`, a new machine isn't refused when the license is on its maximum number of machines: it takes the place of the active machine validated the longest ago, which is deactivated with its `overriddenByMachineId` set to the new machine, and recorded as a `machine.deactivated` event. When a machine deactivated this way is validated again, it takes its place back: the machine that overrode it, and the ones that overrode that one in turn, are locked, with their `overriddenByMachineId` set to the machine coming back. A locked machine is always refused, so two machines can't take turns on one place.  The checks run in this order, and the first one failing answers: the license has expired or was canceled, then it doesn't allow the version, then the machine is locked, then it's on its maximum number of machines. Each failure is recorded as a `license.validation_failed` event, except for keys that don't exist.  Changes to the license, like deactivating the machine or shortening its expiration, don't revoke the tokens already returned: the application only sees them when it validates its key again, at the latest when its token expires.

### Examples

```ruby
require 'time'
require 'license_manager'

api_instance = LicenseManager::LicensesApi.new
product_id = 'x7Kp2QaZ' # String | 
validate_key = LicenseManager::ValidateKey.new({key: '7KQ2M-X9ZPA-H4TRC-WN6EY-B3JDF', fingerprint: '4c:32:75:8f:9a:1e', version: '1.4.2'}) # ValidateKey | 

begin
  # Validate a license key
  result = api_instance.validate_key(product_id, validate_key)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->validate_key: #{e}"
end
```

#### Using the validate_key_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<LicenseToken>, Integer, Hash)> validate_key_with_http_info(product_id, validate_key)

```ruby
begin
  # Validate a license key
  data, status_code, headers = api_instance.validate_key_with_http_info(product_id, validate_key)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <LicenseToken>
rescue LicenseManager::ApiError => e
  puts "Error when calling LicensesApi->validate_key_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **validate_key** | [**ValidateKey**](ValidateKey.md) |  |  |

### Return type

[**LicenseToken**](LicenseToken.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

