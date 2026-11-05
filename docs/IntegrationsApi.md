# LicenseManager::IntegrationsApi

All URIs are relative to *https://api.licensemanager.dev*

| Method | HTTP request | Description |
| ------ | ------------ | ----------- |
| [**authorize_slack**](IntegrationsApi.md#authorize_slack) | **POST** /v1/products/{productId}/integrations/slack/authorize | Start connecting a Slack channel |
| [**check_integration**](IntegrationsApi.md#check_integration) | **POST** /v1/integrations/{id}/check | Check an integration |
| [**connect_stripe**](IntegrationsApi.md#connect_stripe) | **PUT** /v1/products/{productId}/integrations/stripe | Connect Stripe |
| [**create_stripe_mapping**](IntegrationsApi.md#create_stripe_mapping) | **POST** /v1/products/{productId}/integrations/stripe/mappings | Map a Stripe price to a policy |
| [**delete_slack_connection**](IntegrationsApi.md#delete_slack_connection) | **DELETE** /v1/slack-connections/{id} | Remove a Slack connection |
| [**delete_stripe_mapping**](IntegrationsApi.md#delete_stripe_mapping) | **DELETE** /v1/integration-mappings/{id} | Delete a mapping |
| [**disconnect_integration**](IntegrationsApi.md#disconnect_integration) | **DELETE** /v1/integrations/{id} | Disconnect an integration |
| [**get_slack_integration**](IntegrationsApi.md#get_slack_integration) | **GET** /v1/products/{productId}/integrations/slack | Get the Slack integration of a product |
| [**get_stripe_integration**](IntegrationsApi.md#get_stripe_integration) | **GET** /v1/products/{productId}/integrations/stripe | Get the Stripe integration of a product |
| [**list_stripe_prices**](IntegrationsApi.md#list_stripe_prices) | **GET** /v1/integrations/{id}/stripe/prices | List the Stripe prices of an integration |
| [**test_slack_connection**](IntegrationsApi.md#test_slack_connection) | **POST** /v1/slack-connections/{id}/test | Send a test message to a Slack channel |
| [**update_integration**](IntegrationsApi.md#update_integration) | **PATCH** /v1/integrations/{id} | Update an integration |
| [**update_slack_connection**](IntegrationsApi.md#update_slack_connection) | **PATCH** /v1/slack-connections/{id} | Update a Slack connection |
| [**update_stripe_mapping**](IntegrationsApi.md#update_stripe_mapping) | **PATCH** /v1/integration-mappings/{id} | Change the policy of a mapping |


## authorize_slack

> <SlackAuthorize> authorize_slack(product_id)

Start connecting a Slack channel

Returns the URL of Slack's consent screen, where the user picks the channel getting the product's notifications. Slack then redirects to the app's integrations page. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
product_id = 'x7Kp2QaZ' # String | 

begin
  # Start connecting a Slack channel
  result = api_instance.authorize_slack(product_id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->authorize_slack: #{e}"
end
```

#### Using the authorize_slack_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SlackAuthorize>, Integer, Hash)> authorize_slack_with_http_info(product_id)

```ruby
begin
  # Start connecting a Slack channel
  data, status_code, headers = api_instance.authorize_slack_with_http_info(product_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SlackAuthorize>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->authorize_slack_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |

### Return type

[**SlackAuthorize**](SlackAuthorize.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## check_integration

> <Integration> check_integration(id)

Check an integration

Checks right away, as done every day, that the API key still works and can manage the webhook endpoint, which is pointed at the server's webhook URL again (or created again when it was deleted). Updates the status. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 

begin
  # Check an integration
  result = api_instance.check_integration(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->check_integration: #{e}"
end
```

#### Using the check_integration_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Integration>, Integer, Hash)> check_integration_with_http_info(id)

```ruby
begin
  # Check an integration
  data, status_code, headers = api_instance.check_integration_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Integration>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->check_integration_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**Integration**](Integration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## connect_stripe

> <StripeIntegration> connect_stripe(product_id, connect_stripe)

Connect Stripe

Connects the Stripe account of the API key for the organization's products of the product's mode, or replaces the key of the existing connection. Checks the key works and has the required permissions, then creates a webhook endpoint on the account, telling the app about payments. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:create` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
product_id = 'x7Kp2QaZ' # String | 
connect_stripe = LicenseManager::ConnectStripe.new({api_key: 'rk_live_51Nv0FG…'}) # ConnectStripe | 

begin
  # Connect Stripe
  result = api_instance.connect_stripe(product_id, connect_stripe)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->connect_stripe: #{e}"
end
```

#### Using the connect_stripe_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<StripeIntegration>, Integer, Hash)> connect_stripe_with_http_info(product_id, connect_stripe)

```ruby
begin
  # Connect Stripe
  data, status_code, headers = api_instance.connect_stripe_with_http_info(product_id, connect_stripe)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <StripeIntegration>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->connect_stripe_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **connect_stripe** | [**ConnectStripe**](ConnectStripe.md) |  |  |

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## create_stripe_mapping

> <IntegrationMapping> create_stripe_mapping(product_id, create_integration_mapping)

Map a Stripe price to a policy

Paying the price then creates licenses of the product with the policy: one per unit bought. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
product_id = 'x7Kp2QaZ' # String | 
create_integration_mapping = LicenseManager::CreateIntegrationMapping.new({stripe_price_id: 'price_1MoBy5LkdIwHu7ix', policy_id: 'p4Rt8LmQ'}) # CreateIntegrationMapping | 

begin
  # Map a Stripe price to a policy
  result = api_instance.create_stripe_mapping(product_id, create_integration_mapping)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->create_stripe_mapping: #{e}"
end
```

#### Using the create_stripe_mapping_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IntegrationMapping>, Integer, Hash)> create_stripe_mapping_with_http_info(product_id, create_integration_mapping)

```ruby
begin
  # Map a Stripe price to a policy
  data, status_code, headers = api_instance.create_stripe_mapping_with_http_info(product_id, create_integration_mapping)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IntegrationMapping>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->create_stripe_mapping_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |
| **create_integration_mapping** | [**CreateIntegrationMapping**](CreateIntegrationMapping.md) |  |  |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## delete_slack_connection

> delete_slack_connection(id)

Remove a Slack connection

Stops posting to the channel and revokes the installation's token in Slack. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 's4Hq8ZpLm' # String | 

begin
  # Remove a Slack connection
  api_instance.delete_slack_connection(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->delete_slack_connection: #{e}"
end
```

#### Using the delete_slack_connection_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_slack_connection_with_http_info(id)

```ruby
begin
  # Remove a Slack connection
  data, status_code, headers = api_instance.delete_slack_connection_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->delete_slack_connection_with_http_info: #{e}"
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


## delete_stripe_mapping

> delete_stripe_mapping(id)

Delete a mapping

Paying the price no longer creates licenses. The licenses it created stay. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 

begin
  # Delete a mapping
  api_instance.delete_stripe_mapping(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->delete_stripe_mapping: #{e}"
end
```

#### Using the delete_stripe_mapping_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> delete_stripe_mapping_with_http_info(id)

```ruby
begin
  # Delete a mapping
  data, status_code, headers = api_instance.delete_stripe_mapping_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->delete_stripe_mapping_with_http_info: #{e}"
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


## disconnect_integration

> disconnect_integration(id)

Disconnect an integration

Deletes the webhook endpoint from the Stripe account first, then the integration with its mappings, for every product. The endpoint is skipped when it's already gone or the key no longer works; otherwise, when it can't be deleted, the integration is kept. The licenses it created stay. Revoke the API key in Stripe afterwards. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:delete` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 

begin
  # Disconnect an integration
  api_instance.disconnect_integration(id)
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->disconnect_integration: #{e}"
end
```

#### Using the disconnect_integration_with_http_info variant

This returns an Array which contains the response data (`nil` in this case), status code and headers.

> <Array(nil, Integer, Hash)> disconnect_integration_with_http_info(id)

```ruby
begin
  # Disconnect an integration
  data, status_code, headers = api_instance.disconnect_integration_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => nil
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->disconnect_integration_with_http_info: #{e}"
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


## get_slack_integration

> <SlackIntegration> get_slack_integration(product_id)

Get the Slack integration of a product

Slack channels getting notifications about the product's licenses: purchases, renewals, failed payments and cancellations. Doesn't accept tokens: only API keys and sessions.

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

api_instance = LicenseManager::IntegrationsApi.new
product_id = 'x7Kp2QaZ' # String | 

begin
  # Get the Slack integration of a product
  result = api_instance.get_slack_integration(product_id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->get_slack_integration: #{e}"
end
```

#### Using the get_slack_integration_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SlackIntegration>, Integer, Hash)> get_slack_integration_with_http_info(product_id)

```ruby
begin
  # Get the Slack integration of a product
  data, status_code, headers = api_instance.get_slack_integration_with_http_info(product_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SlackIntegration>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->get_slack_integration_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |

### Return type

[**SlackIntegration**](SlackIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## get_stripe_integration

> <StripeIntegration> get_stripe_integration(product_id)

Get the Stripe integration of a product

The organization connects one Stripe account for its live products, and one in test mode for its test products. Its mappings tell which Stripe prices create licenses of the product. Doesn't accept tokens: only API keys and sessions.

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

api_instance = LicenseManager::IntegrationsApi.new
product_id = 'x7Kp2QaZ' # String | 

begin
  # Get the Stripe integration of a product
  result = api_instance.get_stripe_integration(product_id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->get_stripe_integration: #{e}"
end
```

#### Using the get_stripe_integration_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<StripeIntegration>, Integer, Hash)> get_stripe_integration_with_http_info(product_id)

```ruby
begin
  # Get the Stripe integration of a product
  data, status_code, headers = api_instance.get_stripe_integration_with_http_info(product_id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <StripeIntegration>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->get_stripe_integration_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **product_id** | **String** |  |  |

### Return type

[**StripeIntegration**](StripeIntegration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## list_stripe_prices

> <ListStripePrices200Response> list_stripe_prices(id)

List the Stripe prices of an integration

Active one-time prices of active products of the Stripe account, the ones that can be mapped, up to 500. Doesn't accept tokens: only API keys and sessions.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 

begin
  # List the Stripe prices of an integration
  result = api_instance.list_stripe_prices(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->list_stripe_prices: #{e}"
end
```

#### Using the list_stripe_prices_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<ListStripePrices200Response>, Integer, Hash)> list_stripe_prices_with_http_info(id)

```ruby
begin
  # List the Stripe prices of an integration
  data, status_code, headers = api_instance.list_stripe_prices_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <ListStripePrices200Response>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->list_stripe_prices_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**ListStripePrices200Response**](ListStripePrices200Response.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## test_slack_connection

> <SlackConnection> test_slack_connection(id)

Send a test message to a Slack channel

Posts a message to the channel, to check it gets the notifications. Marks the connection `revoked` when Slack says it won't work again. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 's4Hq8ZpLm' # String | 

begin
  # Send a test message to a Slack channel
  result = api_instance.test_slack_connection(id)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->test_slack_connection: #{e}"
end
```

#### Using the test_slack_connection_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SlackConnection>, Integer, Hash)> test_slack_connection_with_http_info(id)

```ruby
begin
  # Send a test message to a Slack channel
  data, status_code, headers = api_instance.test_slack_connection_with_http_info(id)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SlackConnection>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->test_slack_connection_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |

### Return type

[**SlackConnection**](SlackConnection.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json


## update_integration

> <Integration> update_integration(id, update_integration)

Update an integration

Changes the settings of the integration, for every product of its mode. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 
update_integration = LicenseManager::UpdateIntegration.new # UpdateIntegration | 

begin
  # Update an integration
  result = api_instance.update_integration(id, update_integration)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_integration: #{e}"
end
```

#### Using the update_integration_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<Integration>, Integer, Hash)> update_integration_with_http_info(id, update_integration)

```ruby
begin
  # Update an integration
  data, status_code, headers = api_instance.update_integration_with_http_info(id, update_integration)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <Integration>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_integration_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_integration** | [**UpdateIntegration**](UpdateIntegration.md) |  |  |

### Return type

[**Integration**](Integration.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## update_slack_connection

> <SlackConnection> update_slack_connection(id, update_slack_connection)

Update a Slack connection

Changes the notifications the channel gets. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 's4Hq8ZpLm' # String | 
update_slack_connection = LicenseManager::UpdateSlackConnection.new({events: [purchased,  canceled]}) # UpdateSlackConnection | 

begin
  # Update a Slack connection
  result = api_instance.update_slack_connection(id, update_slack_connection)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_slack_connection: #{e}"
end
```

#### Using the update_slack_connection_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<SlackConnection>, Integer, Hash)> update_slack_connection_with_http_info(id, update_slack_connection)

```ruby
begin
  # Update a Slack connection
  data, status_code, headers = api_instance.update_slack_connection_with_http_info(id, update_slack_connection)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <SlackConnection>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_slack_connection_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_slack_connection** | [**UpdateSlackConnection**](UpdateSlackConnection.md) |  |  |

### Return type

[**SlackConnection**](SlackConnection.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json


## update_stripe_mapping

> <IntegrationMapping> update_stripe_mapping(id, update_integration_mapping)

Change the policy of a mapping

Only affects the licenses created afterwards. Doesn't accept tokens: only API keys and sessions.  **Required role permission**: `integration:update` when called with a session, granted by the member's role. API keys aren't limited by roles.

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

api_instance = LicenseManager::IntegrationsApi.new
id = 'i8Fz4QnRt' # String | 
update_integration_mapping = LicenseManager::UpdateIntegrationMapping.new({policy_id: 'p4Rt8LmQ'}) # UpdateIntegrationMapping | 

begin
  # Change the policy of a mapping
  result = api_instance.update_stripe_mapping(id, update_integration_mapping)
  p result
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_stripe_mapping: #{e}"
end
```

#### Using the update_stripe_mapping_with_http_info variant

This returns an Array which contains the response data, status code and headers.

> <Array(<IntegrationMapping>, Integer, Hash)> update_stripe_mapping_with_http_info(id, update_integration_mapping)

```ruby
begin
  # Change the policy of a mapping
  data, status_code, headers = api_instance.update_stripe_mapping_with_http_info(id, update_integration_mapping)
  p status_code # => 2xx
  p headers # => { ... }
  p data # => <IntegrationMapping>
rescue LicenseManager::ApiError => e
  puts "Error when calling IntegrationsApi->update_stripe_mapping_with_http_info: #{e}"
end
```

### Parameters

| Name | Type | Description | Notes |
| ---- | ---- | ----------- | ----- |
| **id** | **String** |  |  |
| **update_integration_mapping** | [**UpdateIntegrationMapping**](UpdateIntegrationMapping.md) |  |  |

### Return type

[**IntegrationMapping**](IntegrationMapping.md)

### Authorization

[apiKey](../README.md#apiKey)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

