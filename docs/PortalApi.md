# LicenseManager::PortalApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**create_portal_link**](PortalApi.md#create_portal_link) | **POST** /v1/customers/{id}/portal-links | Create a link to the customer portal |
| [**get_portal**](PortalApi.md#get_portal) | **GET** /v1/portal/{productId} | Get the customer portal of a product |
| [**request_portal_link**](PortalApi.md#request_portal_link) | **POST** /v1/portal/{productId}/request-link | Email a link to the customer portal |
| [**send_portal_link**](PortalApi.md#send_portal_link) | **POST** /v1/customers/{id}/portal-links/send | Email a link to the customer portal to the customer |


## create_portal_link

> <PortalLink> create_portal_link(id, create_portal_link)

Create a link to the customer portal

Link letting the customer see their licenses and deactivate their machines in the customer portal, without signing in. Anyone with the link can, until it expires or the customer is deleted: it can't be revoked otherwise. The token also works with the API endpoints that accept customer tokens.  Links can be created while the product's customer portal is disabled, but the portal answers `404` until it's enabled, and `sendPortalLink` refuses to email them.  **Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::PortalApi.new
id = 'c9Wd3RtE' # String | 
create_portal_link = LicenseManager::CreatePortalLink.new({expires_in_seconds: 604800}) # CreatePortalLink | 

begin
  # Create a link to the customer portal
  result = api_instance.create_portal_link(id, create_portal_link)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->create_portal_link: #{e}"
end
```

#### Using the create_portal_link_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<PortalLink>, Integer, Hash)> create_portal_link_with_http_info(id, create_portal_link)

```ruby
begin
  # Create a link to the customer portal
  data, status_code, headers = api_instance.create_portal_link_with_http_info(id, create_portal_link)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <PortalLink>
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->create_portal_link_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **create_portal_link** | [**CreatePortalLink**](CreatePortalLink.md) |  |  |

### Return type

[**PortalLink**](PortalLink.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## get_portal

> <Portal> get_portal(product_id, opts)

Get the customer portal of a product

Names of the product and of its organization, colors of the customer portal, and link back to the product's website. Answers `404` when the product's customer portal is disabled: with the `portal_disabled` code and the slugs of the product and its organization when signed in as a member of the organization, so they can enable it. Doesn't need authentication.

### Examples

```ruby
require 'time'
require 'license_manager'

api_instance = LicenseManager::PortalApi.new
product_id = 'x7Kp2QaZ' # String | 
opts = {
  return_url: 'https://example.com/account' # String | Link back to your website to show, used when its domain is one of the product's `returnDomains`.
}

begin
  # Get the customer portal of a product
  result = api_instance.get_portal(product_id, opts)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->get_portal: #{e}"
end
```

#### Using the get_portal_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Portal>, Integer, Hash)> get_portal_with_http_info(product_id, opts)

```ruby
begin
  # Get the customer portal of a product
  data, status_code, headers = api_instance.get_portal_with_http_info(product_id, opts)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Portal>
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->get_portal_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **return_url** | **String** | Link back to your website to show, used when its domain is one of the product&#39;s &#x60;returnDomains&#x60;. | [optional] |

### Return type

[**Portal**](Portal.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## request_portal_link

> request_portal_link(product_id, request_portal_link)

Email a link to the customer portal

Emails the customer of the product with this email a link to the customer portal, working for 1 hour. Answers `404` when the product's customer portal is disabled. Answers the same whether the customer exists or not, so the API doesn't tell which emails are customers. Test products only email the members of the organization: the link isn't sent to other customers, with the same answer. Doesn't need authentication.

### Examples

```ruby
require 'time'
require 'license_manager'

api_instance = LicenseManager::PortalApi.new
product_id = 'x7Kp2QaZ' # String | 
request_portal_link = LicenseManager::RequestPortalLink.new({email: 'jane@example.com'}) # RequestPortalLink | 

begin
  # Email a link to the customer portal
  api_instance.request_portal_link(product_id, request_portal_link)
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->request_portal_link: #{e}"
end
```

#### Using the request_portal_link_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> request_portal_link_with_http_info(product_id, request_portal_link)

```ruby
begin
  # Email a link to the customer portal
  data, status_code, headers = api_instance.request_portal_link_with_http_info(product_id, request_portal_link)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->request_portal_link_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **request_portal_link** | [**RequestPortalLink**](RequestPortalLink.md) |  |  |

### Return type

nil (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## send_portal_link

> send_portal_link(id, send_portal_link)

Email a link to the customer portal to the customer

Emails a link created with `createPortalLink` to the customer's email. Fails while the product's customer portal is disabled, and, in test products, when the customer's email isn't a member's of the organization: test products only email members, so testing never emails real customers.  **Required role permission**: `portalLink:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::PortalApi.new
id = 'c9Wd3RtE' # String | 
send_portal_link = LicenseManager::SendPortalLink.new({token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9…'}) # SendPortalLink | 

begin
  # Email a link to the customer portal to the customer
  api_instance.send_portal_link(id, send_portal_link)
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->send_portal_link: #{e}"
end
```

#### Using the send_portal_link_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> send_portal_link_with_http_info(id, send_portal_link)

```ruby
begin
  # Email a link to the customer portal to the customer
  data, status_code, headers = api_instance.send_portal_link_with_http_info(id, send_portal_link)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling PortalApi->send_portal_link_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **send_portal_link** | [**SendPortalLink**](SendPortalLink.md) |  |  |

### Return type

nil (empty response body)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

