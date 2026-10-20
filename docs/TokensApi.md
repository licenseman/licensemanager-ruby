# LicenseManager::TokensApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_customer_token**](TokensApi.md#create_customer_token) | **POST** /v1/customers/{id}/tokens | Create a customer token |
| [**create_license_token**](TokensApi.md#create_license_token) | **POST** /v1/licenses/{id}/tokens | Create a license token |
| [**create_machine_token**](TokensApi.md#create_machine_token) | **POST** /v1/machines/{id}/tokens | Create a machine token |


## create_customer_token

> <Token> create_customer_token(id, create_token)

Create a customer token

Creates a token scoped to the customer, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::TokensApi.new
id = 'c9Wd3RtE' # String | 
create_token = LicenseManager::CreateToken.new({scope: [license: read,  machine: write]}) # CreateToken | 

begin
  # Create a customer token
  result = api_instance.create_customer_token(id, create_token)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_customer_token: #{e}"
end
```

#### Using the create_customer_token_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Token>, Integer, Hash)> create_customer_token_with_http_info(id, create_token)

```ruby
begin
  # Create a customer token
  data, status_code, headers = api_instance.create_customer_token_with_http_info(id, create_token)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Token>
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_customer_token_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **create_token** | [**CreateToken**](CreateToken.md) |  |  |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## create_license_token

> <Token> create_license_token(id, create_token)

Create a license token

Creates a token scoped to the license, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Token access**: customer tokens. A customer token creates tokens for its customer's licenses, with the permissions and at most the expiration it has.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::TokensApi.new
id = 'c9Wd3RtE' # String | 
create_token = LicenseManager::CreateToken.new({scope: [license: read,  machine: write]}) # CreateToken | 

begin
  # Create a license token
  result = api_instance.create_license_token(id, create_token)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_license_token: #{e}"
end
```

#### Using the create_license_token_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Token>, Integer, Hash)> create_license_token_with_http_info(id, create_token)

```ruby
begin
  # Create a license token
  data, status_code, headers = api_instance.create_license_token_with_http_info(id, create_token)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Token>
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_license_token_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **create_token** | [**CreateToken**](CreateToken.md) |  |  |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## create_machine_token

> <Token> create_machine_token(id, create_token)

Create a machine token

Creates a token scoped to the machine, with the permissions of `scope`, to hand to your customers: a page of your website can then call the endpoints accepting tokens directly, without your API key. See the `token` security scheme for what a token reaches.  A token can't be revoked: it works until it expires, unless the resource it's scoped to is deleted.  **Token access**: customer, license tokens. A customer or license token creates tokens for the machines it reaches, with the permissions and at most the expiration it has.  **Required role permission**: `token:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::TokensApi.new
id = 'c9Wd3RtE' # String | 
create_token = LicenseManager::CreateToken.new({scope: [license: read,  machine: write]}) # CreateToken | 

begin
  # Create a machine token
  result = api_instance.create_machine_token(id, create_token)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_machine_token: #{e}"
end
```

#### Using the create_machine_token_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Token>, Integer, Hash)> create_machine_token_with_http_info(id, create_token)

```ruby
begin
  # Create a machine token
  data, status_code, headers = api_instance.create_machine_token_with_http_info(id, create_token)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Token>
rescue LicenseManager::ApiError => e
  puts "Error when calling TokensApi->create_machine_token_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **create_token** | [**CreateToken**](CreateToken.md) |  |  |

### Return type

[**Token**](Token.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

