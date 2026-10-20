# LicenseManager::CustomersApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_customer**](CustomersApi.md#create_customer) | **POST** /v1/products/{productId}/customers | Create a customer |
| [**delete_customer**](CustomersApi.md#delete_customer) | **DELETE** /v1/customers/{id} | Delete a customer |
| [**get_customer**](CustomersApi.md#get_customer) | **GET** /v1/customers/{id} | Get a customer |
| [**list_customers**](CustomersApi.md#list_customers) | **GET** /v1/products/{productId}/customers | List the customers of a product |
| [**update_customer**](CustomersApi.md#update_customer) | **PATCH** /v1/customers/{id} | Update a customer |


## create_customer

> <Customer> create_customer(product_id, create_customer)

Create a customer

**Required role permission**: `customer:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::CustomersApi.new
product_id = 'x7Kp2QaZ' # String | 
create_customer = LicenseManager::CreateCustomer.new({email: 'jane@example.com'}) # CreateCustomer | 

begin
  # Create a customer
  result = api_instance.create_customer(product_id, create_customer)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->create_customer: #{e}"
end
```

#### Using the create_customer_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Customer>, Integer, Hash)> create_customer_with_http_info(product_id, create_customer)

```ruby
begin
  # Create a customer
  data, status_code, headers = api_instance.create_customer_with_http_info(product_id, create_customer)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Customer>
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->create_customer_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **create_customer** | [**CreateCustomer**](CreateCustomer.md) |  |  |

### Return type

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_customer

> delete_customer(id)

Delete a customer

A customer that licenses belong to can't be deleted: delete them first. The customer tokens of the customer, like the ones of its portal links, stop working.  **Required role permission**: `customer:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::CustomersApi.new
id = 'c9Wd3RtE' # String | 

begin
  # Delete a customer
  api_instance.delete_customer(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->delete_customer: #{e}"
end
```

#### Using the delete_customer_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_customer_with_http_info(id)

```ruby
begin
  # Delete a customer
  data, status_code, headers = api_instance.delete_customer_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->delete_customer_with_http_info: #{e}"
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


## get_customer

> <Customer> get_customer(id)

Get a customer

**Token access**: customer, license, machine tokens with the `customer:read` permission (or the matching write one). A token reaches the customer it's scoped to, or the customer of its license or machine.

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

api_instance = LicenseManager::CustomersApi.new
id = 'c9Wd3RtE' # String | 

begin
  # Get a customer
  result = api_instance.get_customer(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->get_customer: #{e}"
end
```

#### Using the get_customer_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Customer>, Integer, Hash)> get_customer_with_http_info(id)

```ruby
begin
  # Get a customer
  data, status_code, headers = api_instance.get_customer_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Customer>
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->get_customer_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_customers

> <CustomerList> list_customers(product_id, opts)

List the customers of a product

Sorting by `name` puts the customers without a name last in both orders.

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

api_instance = LicenseManager::CustomersApi.new
product_id = 'x7Kp2QaZ' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'name', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  search: 'example.com', # String | Case-insensitive text the name or email contains.
  email: 'jane@example.com' # String | Only returns the customer with this email, compared regardless of case.
}

begin
  # List the customers of a product
  result = api_instance.list_customers(product_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->list_customers: #{e}"
end
```

#### Using the list_customers_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<CustomerList>, Integer, Hash)> list_customers_with_http_info(product_id, opts)

```ruby
begin
  # List the customers of a product
  data, status_code, headers = api_instance.list_customers_with_http_info(product_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <CustomerList>
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->list_customers_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **search** | **String** | Case-insensitive text the name or email contains. | [optional] |
| **email** | **String** | Only returns the customer with this email, compared regardless of case. | [optional] |

### Return type

[**CustomerList**](CustomerList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_customer

> <Customer> update_customer(id, update_customer)

Update a customer

**Required role permission**: `customer:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::CustomersApi.new
id = 'c9Wd3RtE' # String | 
update_customer = LicenseManager::UpdateCustomer.new # UpdateCustomer | 

begin
  # Update a customer
  result = api_instance.update_customer(id, update_customer)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->update_customer: #{e}"
end
```

#### Using the update_customer_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Customer>, Integer, Hash)> update_customer_with_http_info(id, update_customer)

```ruby
begin
  # Update a customer
  data, status_code, headers = api_instance.update_customer_with_http_info(id, update_customer)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Customer>
rescue LicenseManager::ApiError => e
  puts "Error when calling CustomersApi->update_customer_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_customer** | [**UpdateCustomer**](UpdateCustomer.md) |  |  |

### Return type

[**Customer**](Customer.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

