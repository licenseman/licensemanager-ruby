# LicenseManager::MachinesApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**deactivate_machine**](MachinesApi.md#deactivate_machine) | **POST** /v1/machines/{id}/deactivate | Deactivate a machine |
| [**get_machine**](MachinesApi.md#get_machine) | **GET** /v1/machines/{id} | Get a machine |
| [**list_machines**](MachinesApi.md#list_machines) | **GET** /v1/licenses/{licenseId}/machines | List the machines of a license |


## deactivate_machine

> <Machine> deactivate_machine(id)

Deactivate a machine

The machine no longer counts as using the license, freeing its place when the license has a maximum number of machines. Validating the license key on the machine activates it again, unless the license is on its maximum number of machines by then. Deactivating a deactivated machine does nothing.  The license token `validateKey` returned to the machine isn't revoked: the application can keep running offline until it expires. Machines can't be deleted: they're deleted with their license.  **Token access**: customer, license, machine tokens with the `machine:write` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.  **Required role permission**: `machine:deactivate` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::MachinesApi.new
id = 'm9Tq3VhD' # String | 

begin
  # Deactivate a machine
  result = api_instance.deactivate_machine(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->deactivate_machine: #{e}"
end
```

#### Using the deactivate_machine_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Machine>, Integer, Hash)> deactivate_machine_with_http_info(id)

```ruby
begin
  # Deactivate a machine
  data, status_code, headers = api_instance.deactivate_machine_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Machine>
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->deactivate_machine_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_machine

> <Machine> get_machine(id)

Get a machine

**Token access**: customer, license, machine tokens with the `machine:read` permission (or the matching write one). A token reaches the machine it's scoped to, or the machines of its license or customer.

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

api_instance = LicenseManager::MachinesApi.new
id = 'm9Tq3VhD' # String | 

begin
  # Get a machine
  result = api_instance.get_machine(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->get_machine: #{e}"
end
```

#### Using the get_machine_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Machine>, Integer, Hash)> get_machine_with_http_info(id)

```ruby
begin
  # Get a machine
  data, status_code, headers = api_instance.get_machine_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Machine>
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->get_machine_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Machine**](Machine.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_machines

> <MachineList> list_machines(license_id, opts)

List the machines of a license

**Token access**: customer, license tokens with the `machine:read` permission (or the matching write one). A token reaches the license it's scoped to, or the licenses of its customer.

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

api_instance = LicenseManager::MachinesApi.new
license_id = 'l3Nv8KwB' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'name', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  search: 'macbook', # String | Case-insensitive text the fingerprint or name contains.
  fingerprint: '4c:32:75:8f:9a:1e', # String | Only returns the machine with this exact fingerprint.
  status: 'active' # String | Only returns the machines with this status.
}

begin
  # List the machines of a license
  result = api_instance.list_machines(license_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->list_machines: #{e}"
end
```

#### Using the list_machines_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<MachineList>, Integer, Hash)> list_machines_with_http_info(license_id, opts)

```ruby
begin
  # List the machines of a license
  data, status_code, headers = api_instance.list_machines_with_http_info(license_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <MachineList>
rescue LicenseManager::ApiError => e
  puts "Error when calling MachinesApi->list_machines_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **license_id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **search** | **String** | Case-insensitive text the fingerprint or name contains. | [optional] |
| **fingerprint** | **String** | Only returns the machine with this exact fingerprint. | [optional] |
| **status** | **String** | Only returns the machines with this status. | [optional] |

### Return type

[**MachineList**](MachineList.md)

### Authorization

[apiKey](../README.md#apiKey), [token](../README.md#token)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

