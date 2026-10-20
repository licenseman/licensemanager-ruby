# LicenseManager::EventActor

## Class instance methods

### `openapi_one_of`

Returns the list of classes defined in oneOf.

#### Example

```ruby
require 'license_manager'

LicenseManager::EventActor.openapi_one_of
# =>
# [
#   :'EventActorOneOf',
#   :'EventActorOneOf1',
#   :'EventActorOneOf2',
#   :'EventActorOneOf3',
#   :'EventActorOneOf4'
# ]
```

### build

Find the appropriate object from the `openapi_one_of` list and casts the data into it.

#### Example

```ruby
require 'license_manager'

LicenseManager::EventActor.build(data)
# => #<EventActorOneOf:0x00007fdd4aab02a0>

LicenseManager::EventActor.build(data_that_doesnt_match)
# => nil
```

#### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| **data** | **Mixed** | data to be matched against the list of oneOf items |

#### Return type

- `EventActorOneOf`
- `EventActorOneOf1`
- `EventActorOneOf2`
- `EventActorOneOf3`
- `EventActorOneOf4`
- `nil` (if no type matches)

