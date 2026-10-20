# LicenseManager::PoliciesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_policy**](PoliciesApi.md#create_policy) | **POST** /v1/products/{productId}/policies | Create a policy |
| [**delete_policy**](PoliciesApi.md#delete_policy) | **DELETE** /v1/policies/{id} | Delete a policy |
| [**get_policy**](PoliciesApi.md#get_policy) | **GET** /v1/policies/{id} | Get a policy |
| [**list_policies**](PoliciesApi.md#list_policies) | **GET** /v1/products/{productId}/policies | List the policies of a product |
| [**update_policy**](PoliciesApi.md#update_policy) | **PATCH** /v1/policies/{id} | Update a policy |


## create_policy

> <Policy> create_policy(product_id, create_policy)

Create a policy

Without a `slug`, the policy gets one derived from its name, made unique within the product by appending a dash and 3 random lowercase letters or digits when needed. An explicit `slug` is used as is: the request fails with a `409` when it's taken.  With `isDefault: true`, the new policy replaces the product's current default policy.  A product always has a default policy, so when it has no policies the new one becomes the default: the request fails with a `409` when `isDefault` is `false`.  **Required role permission**: `policy:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::PoliciesApi.new
product_id = 'x7Kp2QaZ' # String | 
create_policy = LicenseManager::CreatePolicy.new({name: 'Yearly'}) # CreatePolicy | 

begin
  # Create a policy
  result = api_instance.create_policy(product_id, create_policy)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->create_policy: #{e}"
end
```

#### Using the create_policy_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Policy>, Integer, Hash)> create_policy_with_http_info(product_id, create_policy)

```ruby
begin
  # Create a policy
  data, status_code, headers = api_instance.create_policy_with_http_info(product_id, create_policy)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Policy>
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->create_policy_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **create_policy** | [**CreatePolicy**](CreatePolicy.md) |  |  |

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_policy

> delete_policy(id)

Delete a policy

Deleting the default policy makes the oldest remaining policy of the product the default. The last policy of a product can't be deleted, nor a policy that licenses follow. Its events can no longer be listed.  **Required role permission**: `policy:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::PoliciesApi.new
id = 'p4Rt8LmQ' # String | 

begin
  # Delete a policy
  api_instance.delete_policy(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->delete_policy: #{e}"
end
```

#### Using the delete_policy_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_policy_with_http_info(id)

```ruby
begin
  # Delete a policy
  data, status_code, headers = api_instance.delete_policy_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->delete_policy_with_http_info: #{e}"
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


## get_policy

> <Policy> get_policy(id)

Get a policy

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

api_instance = LicenseManager::PoliciesApi.new
id = 'p4Rt8LmQ' # String | 

begin
  # Get a policy
  result = api_instance.get_policy(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->get_policy: #{e}"
end
```

#### Using the get_policy_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Policy>, Integer, Hash)> get_policy_with_http_info(id)

```ruby
begin
  # Get a policy
  data, status_code, headers = api_instance.get_policy_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Policy>
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->get_policy_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_policies

> <PolicyList> list_policies(product_id, opts)

List the policies of a product

`?isDefault=true` returns the product's default policy alone: a product always has exactly one. Sorting by `duration` counts months for their average length, about 30.4 days.

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

api_instance = LicenseManager::PoliciesApi.new
product_id = 'x7Kp2QaZ' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'name', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `name`.
  search: 'pro', # String | Case-insensitive text the name or slug contains.
  slug: 'yearly', # String | Only returns the policy with this exact slug.
  is_default: 'true', # String | `true` only returns the product's default policy, `false` only the other ones.
  license_count: 1, # Integer | Only returns the policies followed by exactly this number of licenses.
  license_count_min: 1, # Integer | Only returns the policies followed by at least this number of licenses.
  license_count_max: 1 # Integer | Only returns the policies followed by at most this number of licenses.
}

begin
  # List the policies of a product
  result = api_instance.list_policies(product_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->list_policies: #{e}"
end
```

#### Using the list_policies_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<PolicyList>, Integer, Hash)> list_policies_with_http_info(product_id, opts)

```ruby
begin
  # List the policies of a product
  data, status_code, headers = api_instance.list_policies_with_http_info(product_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <PolicyList>
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->list_policies_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;name&#x60;. | [optional][default to &#39;name&#39;] |
| **search** | **String** | Case-insensitive text the name or slug contains. | [optional] |
| **slug** | **String** | Only returns the policy with this exact slug. | [optional] |
| **is_default** | **String** | &#x60;true&#x60; only returns the product&#39;s default policy, &#x60;false&#x60; only the other ones. | [optional] |
| **license_count** | **Integer** | Only returns the policies followed by exactly this number of licenses. | [optional] |
| **license_count_min** | **Integer** | Only returns the policies followed by at least this number of licenses. | [optional] |
| **license_count_max** | **Integer** | Only returns the policies followed by at most this number of licenses. | [optional] |

### Return type

[**PolicyList**](PolicyList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_policy

> <Policy> update_policy(id, update_policy)

Update a policy

`isDefault: true` makes the policy the product's default, in place of the current one. A product always has a default policy, so the default can't be unset with `isDefault: false`: make another policy the default instead.  Licenses copy the settings of their policy when they're created, so changing them only affects the licenses created afterwards: update the existing licenses to change theirs.  **Required role permission**: `policy:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::PoliciesApi.new
id = 'p4Rt8LmQ' # String | 
update_policy = LicenseManager::UpdatePolicy.new # UpdatePolicy | 

begin
  # Update a policy
  result = api_instance.update_policy(id, update_policy)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->update_policy: #{e}"
end
```

#### Using the update_policy_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Policy>, Integer, Hash)> update_policy_with_http_info(id, update_policy)

```ruby
begin
  # Update a policy
  data, status_code, headers = api_instance.update_policy_with_http_info(id, update_policy)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Policy>
rescue LicenseManager::ApiError => e
  puts "Error when calling PoliciesApi->update_policy_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_policy** | [**UpdatePolicy**](UpdatePolicy.md) |  |  |

### Return type

[**Policy**](Policy.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

