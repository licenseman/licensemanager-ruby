# LicenseManager::ProductsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_product**](ProductsApi.md#create_product) | **POST** /v1/products | Create a product |
| [**delete_product**](ProductsApi.md#delete_product) | **DELETE** /v1/products/{id} | Delete a product |
| [**delete_product_logo**](ProductsApi.md#delete_product_logo) | **DELETE** /v1/products/{id}/logo | Delete a product logo |
| [**get_product**](ProductsApi.md#get_product) | **GET** /v1/products/{id} | Get a product |
| [**get_product_stats**](ProductsApi.md#get_product_stats) | **GET** /v1/products/{id}/stats | Get the stats of a product |
| [**list_products**](ProductsApi.md#list_products) | **GET** /v1/products | List products |
| [**reset_product**](ProductsApi.md#reset_product) | **POST** /v1/products/{id}/reset | Reset a test product |
| [**update_product**](ProductsApi.md#update_product) | **PATCH** /v1/products/{id} | Update a product |
| [**upload_product_logo**](ProductsApi.md#upload_product_logo) | **PUT** /v1/products/{id}/logo | Upload a product logo |


## create_product

> <Product> create_product(create_product_with_policy)

Create a product

Without a `slug`, the product gets one derived from its name: lower cased, without accents and special characters (`Élan Pro 2!` becomes `elan-pro-2`). When another product of the organization already uses it, a dash and 3 random lowercase letters or digits are appended (`elan-pro-2-k3f`), until the slug is free.  An explicit `slug` is used as is: the request fails with a `409` when it's taken, it's never changed.  Slug uniqueness is enforced by the database, so when concurrent requests end up with the same slug, only one succeeds and the others get a `409`, even without an explicit `slug`. Retrying such a request without a `slug` derives a new one.  The product is created with its default policy, named `Default policy` with the `default` slug, whose settings are given by `defaultPolicy`. Omitted settings default to licenses that never expire, on a single machine, offline for one week, for every version of the product. Unlike `createPolicy`, where `maxMachines` defaults to no limit.  With `isTestFromProductId`, the product is a test product: its id, its slug, and the ids, slugs and license keys of its resources start with `test_` (`TEST-` for license keys), and only test API keys reach it. It starts with copies of the policies, releases, portal settings and `autoMachineChange` of the live product, `defaultPolicy` is ignored. Later changes to the live product aren't copied: reset the test product to copy them again. Test API keys can only create test products, live API keys only live ones.  **Required role permission**: `product:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
create_product_with_policy = LicenseManager::CreateProductWithPolicy.new({name: 'Acme Pro'}) # CreateProductWithPolicy | 

begin
  # Create a product
  result = api_instance.create_product(create_product_with_policy)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->create_product: #{e}"
end
```

#### Using the create_product_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> create_product_with_http_info(create_product_with_policy)

```ruby
begin
  # Create a product
  data, status_code, headers = api_instance.create_product_with_http_info(create_product_with_policy)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->create_product_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **create_product_with_policy** | [**CreateProductWithPolicy**](CreateProductWithPolicy.md) |  |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_product

> delete_product(id)

Delete a product

Deletes the product along with its policies, customers and releases, and its test products with everything they hold. A live product that licenses belong to can't be deleted: delete them first. A test product can always be deleted, along with its licenses and machines. The events of the deleted policies and licenses can no longer be listed.  **Required role permission**: `product:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 

begin
  # Delete a product
  api_instance.delete_product(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->delete_product: #{e}"
end
```

#### Using the delete_product_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_product_with_http_info(id)

```ruby
begin
  # Delete a product
  data, status_code, headers = api_instance.delete_product_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->delete_product_with_http_info: #{e}"
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


## delete_product_logo

> <Product> delete_product_logo(id)

Delete a product logo

Removes the logo of the product, and deletes its image. Succeeds when the product has no logo.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 

begin
  # Delete a product logo
  result = api_instance.delete_product_logo(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->delete_product_logo: #{e}"
end
```

#### Using the delete_product_logo_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> delete_product_logo_with_http_info(id)

```ruby
begin
  # Delete a product logo
  data, status_code, headers = api_instance.delete_product_logo_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->delete_product_logo_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_product

> <Product> get_product(id)

Get a product

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 

begin
  # Get a product
  result = api_instance.get_product(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->get_product: #{e}"
end
```

#### Using the get_product_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> get_product_with_http_info(id)

```ruby
begin
  # Get a product
  data, status_code, headers = api_instance.get_product_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->get_product_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_product_stats

> <ProductStats> get_product_stats(id)

Get the stats of a product

Counts of the licenses and machines of the product, number of licenses created each day over the last 30 days and each month over the last 12 months, overall and per policy, revenue per currency over the same periods, and successful activations each day over the last 30 days. Days and months are in UTC.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 

begin
  # Get the stats of a product
  result = api_instance.get_product_stats(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->get_product_stats: #{e}"
end
```

#### Using the get_product_stats_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<ProductStats>, Integer, Hash)> get_product_stats_with_http_info(id)

```ruby
begin
  # Get the stats of a product
  data, status_code, headers = api_instance.get_product_stats_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <ProductStats>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->get_product_stats_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**ProductStats**](ProductStats.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_products

> <ProductList> list_products(opts)

List products

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

api_instance = LicenseManager::ProductsApi.new
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'name', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  search: 'pro', # String | Case-insensitive text the name or slug contains.
  slug: 'acme-pro', # String | Only returns the product with this exact slug.
  is_test: 'true' # String | Only returns the test products with `true`, the live ones with `false`. API keys only list the products of their own mode.
}

begin
  # List products
  result = api_instance.list_products(opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->list_products: #{e}"
end
```

#### Using the list_products_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<ProductList>, Integer, Hash)> list_products_with_http_info(opts)

```ruby
begin
  # List products
  data, status_code, headers = api_instance.list_products_with_http_info(opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <ProductList>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->list_products_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **search** | **String** | Case-insensitive text the name or slug contains. | [optional] |
| **slug** | **String** | Only returns the product with this exact slug. | [optional] |
| **is_test** | **String** | Only returns the test products with &#x60;true&#x60;, the live ones with &#x60;false&#x60;. API keys only list the products of their own mode. | [optional] |

### Return type

[**ProductList**](ProductList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## reset_product

> <Product> reset_product(id)

Reset a test product

Deletes the customers, licenses, machines, policies and releases of the test product, with their events, then copies the policies, releases, portal settings and `autoMachineChange` of its live product again. Its id, name and slug are kept, but the copied policies get new ids. The tokens of its customers, licenses and machines stop working.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 

begin
  # Reset a test product
  result = api_instance.reset_product(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->reset_product: #{e}"
end
```

#### Using the reset_product_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> reset_product_with_http_info(id)

```ruby
begin
  # Reset a test product
  data, status_code, headers = api_instance.reset_product_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->reset_product_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_product

> <Product> update_product(id, update_product)

Update a product

A product can't be turned into a test product, or back: `isTestFromProductId` can't be changed.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 
update_product = LicenseManager::UpdateProduct.new # UpdateProduct | 

begin
  # Update a product
  result = api_instance.update_product(id, update_product)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->update_product: #{e}"
end
```

#### Using the update_product_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> update_product_with_http_info(id, update_product)

```ruby
begin
  # Update a product
  data, status_code, headers = api_instance.update_product_with_http_info(id, update_product)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->update_product_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_product** | [**UpdateProduct**](UpdateProduct.md) |  |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## upload_product_logo

> <Product> upload_product_logo(id, file)

Upload a product logo

Replaces the logo of the product, shown in the web app and the customer portal. The previous logo is deleted.  Accepts WebP, PNG, JPEG and SVG images up to 1 MB, recognized by their content. Logos are shown in squares: use square images, 256×256 pixels for bitmaps. The web app crops and resizes images to this size, and converts them to WebP, before uploading them.  **Required role permission**: `product:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::ProductsApi.new
id = 'x7Kp2QaZ' # String | 
file = File.new('/path/to/some/file') # File | WebP, PNG, JPEG or SVG image, up to 1 MB.

begin
  # Upload a product logo
  result = api_instance.upload_product_logo(id, file)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->upload_product_logo: #{e}"
end
```

#### Using the upload_product_logo_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Product>, Integer, Hash)> upload_product_logo_with_http_info(id, file)

```ruby
begin
  # Upload a product logo
  data, status_code, headers = api_instance.upload_product_logo_with_http_info(id, file)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Product>
rescue LicenseManager::ApiError => e
  puts "Error when calling ProductsApi->upload_product_logo_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **file** | **File** | WebP, PNG, JPEG or SVG image, up to 1 MB. |  |

### Return type

[**Product**](Product.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: multipart/form-data
- **Accept**: application/json

