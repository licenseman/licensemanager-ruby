# LicenseManager::EventsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**list_license_events**](EventsApi.md#list_license_events) | **GET** /v1/licenses/{id}/events | List the events of a license |
| [**list_policy_events**](EventsApi.md#list_policy_events) | **GET** /v1/policies/{id}/events | List the events of a policy |


## list_license_events

> <EventList> list_license_events(id, opts)

List the events of a license

Includes the validations of the license on each of its machines. Doesn't accept tokens: only API keys and sessions.

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

api_instance = LicenseManager::EventsApi.new
id = 'l3Nv8KwB' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'createdAt', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  type: LicenseManager::ListPolicyEventsTypeParameter.new, # ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types.
  machine_id: 'm9Tq3VhD' # String | Only returns the events of this machine of the license.
}

begin
  # List the events of a license
  result = api_instance.list_license_events(id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling EventsApi->list_license_events: #{e}"
end
```

#### Using the list_license_events_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<EventList>, Integer, Hash)> list_license_events_with_http_info(id, opts)

```ruby
begin
  # List the events of a license
  data, status_code, headers = api_instance.list_license_events_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <EventList>
rescue LicenseManager::ApiError => e
  puts "Error when calling EventsApi->list_license_events_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **type** | [**ListPolicyEventsTypeParameter**](.md) | Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] |
| **machine_id** | **String** | Only returns the events of this machine of the license. | [optional] |

### Return type

[**EventList**](EventList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_policy_events

> <EventList> list_policy_events(id, opts)

List the events of a policy

Doesn't accept tokens: only API keys and sessions.

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

api_instance = LicenseManager::EventsApi.new
id = 'l3Nv8KwB' # String | 
opts = {
  page: 1, # Integer | Page to return. Pages are numbered from 1: `1` is the first page. A page past the last one returns an empty `data`, not an error. Defaults to `1`.
  page_size: 20, # Integer | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to `20`.
  sort: 'createdAt', # String | Field to sort by, prefixed with `-` for descending order. Defaults to `-createdAt`.
  type: LicenseManager::ListPolicyEventsTypeParameter.new # ListPolicyEventsTypeParameter | Only returns the events of this type. Repeat it to return the events of any of these types.
}

begin
  # List the events of a policy
  result = api_instance.list_policy_events(id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling EventsApi->list_policy_events: #{e}"
end
```

#### Using the list_policy_events_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<EventList>, Integer, Hash)> list_policy_events_with_http_info(id, opts)

```ruby
begin
  # List the events of a policy
  data, status_code, headers = api_instance.list_policy_events_with_http_info(id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <EventList>
rescue LicenseManager::ApiError => e
  puts "Error when calling EventsApi->list_policy_events_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **page** | **Integer** | Page to return. Pages are numbered from 1: &#x60;1&#x60; is the first page. A page past the last one returns an empty &#x60;data&#x60;, not an error. Defaults to &#x60;1&#x60;. | [optional][default to 1] |
| **page_size** | **Integer** | Maximum number of items per page, from 1 to 100. Every page holds this many items except the last one, which can hold fewer. Defaults to &#x60;20&#x60;. | [optional][default to 20] |
| **sort** | **String** | Field to sort by, prefixed with &#x60;-&#x60; for descending order. Defaults to &#x60;-createdAt&#x60;. | [optional][default to &#39;-createdAt&#39;] |
| **type** | [**ListPolicyEventsTypeParameter**](.md) | Only returns the events of this type. Repeat it to return the events of any of these types. | [optional] |

### Return type

[**EventList**](EventList.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

