# LicenseManager::ReleasesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_release**](ReleasesApi.md#create_release) | **POST** /v1/products/{productId}/releases | Create a release |
| [**delete_release**](ReleasesApi.md#delete_release) | **DELETE** /v1/releases/{id} | Delete a release |
| [**get_release**](ReleasesApi.md#get_release) | **GET** /v1/releases/{id} | Get a release |
| [**list_releases**](ReleasesApi.md#list_releases) | **GET** /v1/products/{productId}/releases | List the releases of a product |
| [**update_release**](ReleasesApi.md#update_release) | **PATCH** /v1/releases/{id} | Update a release |


## create_release

> <Release> create_release(product_id, create_release)

Create a release

Releases don't restrict which versions `validateKey` accepts: a machine can run a version without a release. They give the `latestAllowedVersion` of its `version_not_allowed` errors, among the stable releases already released, and the number of active machines running each version.  **Required role permission**: `release:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ReleasesApi.new
product_id = 'x7Kp2QaZ' # String | 
create_release = LicenseManager::CreateRelease.new({version: '2.3.1'}) # CreateRelease | 

begin
  # Create a release
  result = api_instance.create_release(product_id, create_release)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->create_release: #{e}"
end
```

#### Using the create_release_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Release>, Integer, Hash)> create_release_with_http_info(product_id, create_release)

```ruby
begin
  # Create a release
  data, status_code, headers = api_instance.create_release_with_http_info(product_id, create_release)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Release>
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->create_release_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **create_release** | [**CreateRelease**](CreateRelease.md) |  |  |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_release

> delete_release(id)

Delete a release

**Required role permission**: `release:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ReleasesApi.new
id = 'r4Lm8VwX' # String | 

begin
  # Delete a release
  api_instance.delete_release(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->delete_release: #{e}"
end
```

#### Using the delete_release_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_release_with_http_info(id)

```ruby
begin
  # Delete a release
  data, status_code, headers = api_instance.delete_release_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->delete_release_with_http_info: #{e}"
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


## get_release

> <Release> get_release(id)

Get a release

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

api_instance = LicenseManager::ReleasesApi.new
id = 'r4Lm8VwX' # String | 

begin
  # Get a release
  result = api_instance.get_release(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->get_release: #{e}"
end
```

#### Using the get_release_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Release>, Integer, Hash)> get_release_with_http_info(id)

```ruby
begin
  # Get a release
  data, status_code, headers = api_instance.get_release_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Release>
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->get_release_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_releases

> <ReleaseList> list_releases(product_id, opts)

List the releases of a product

Sorting by `version` compares the major, minor and patch numbers as numbers, then puts a pre-release before its stable release. Pre-releases of the same version compare as text, unlike semantic versioning: `2.0.0-beta.10` comes before `2.0.0-beta.2`. Build metadata is ignored.

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

api_instance = LicenseManager::ReleasesApi.new
product_id = 'x7Kp2QaZ' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'version', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-version`.
  search: '2.3', # String | Case-insensitive text the version contains.
  released_from: Time.parse('2026-01-01T00:00:00.000Z'), # Time | Only returns the releases released at or after this date.
  released_to: Time.parse('2026-02-01T00:00:00.000Z'), # Time | Only returns the releases released at or before this date.
  active_machine_count: 1, # Integer | Only returns the releases running on exactly this number of active machines.
  active_machine_count_min: 1, # Integer | Only returns the releases running on at least this number of active machines.
  active_machine_count_max: 1 # Integer | Only returns the releases running on at most this number of active machines.
}

begin
  # List the releases of a product
  result = api_instance.list_releases(product_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->list_releases: #{e}"
end
```

#### Using the list_releases_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<ReleaseList>, Integer, Hash)> list_releases_with_http_info(product_id, opts)

```ruby
begin
  # List the releases of a product
  data, status_code, headers = api_instance.list_releases_with_http_info(product_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <ReleaseList>
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->list_releases_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-version&#x60;. | [optional][default to &#39;-version&#39;] |
| **search** | **String** | Case-insensitive text the version contains. | [optional] |
| **released_from** | **Time** | Only returns the releases released at or after this date. | [optional] |
| **released_to** | **Time** | Only returns the releases released at or before this date. | [optional] |
| **active_machine_count** | **Integer** | Only returns the releases running on exactly this number of active machines. | [optional] |
| **active_machine_count_min** | **Integer** | Only returns the releases running on at least this number of active machines. | [optional] |
| **active_machine_count_max** | **Integer** | Only returns the releases running on at most this number of active machines. | [optional] |

### Return type

[**ReleaseList**](ReleaseList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_release

> <Release> update_release(id, update_release)

Update a release

**Required role permission**: `release:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ReleasesApi.new
id = 'r4Lm8VwX' # String | 
update_release = LicenseManager::UpdateRelease.new # UpdateRelease | 

begin
  # Update a release
  result = api_instance.update_release(id, update_release)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->update_release: #{e}"
end
```

#### Using the update_release_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Release>, Integer, Hash)> update_release_with_http_info(id, update_release)

```ruby
begin
  # Update a release
  data, status_code, headers = api_instance.update_release_with_http_info(id, update_release)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Release>
rescue LicenseManager::ApiError => e
  puts "Error when calling ReleasesApi->update_release_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_release** | [**UpdateRelease**](UpdateRelease.md) |  |  |

### Return type

[**Release**](Release.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

