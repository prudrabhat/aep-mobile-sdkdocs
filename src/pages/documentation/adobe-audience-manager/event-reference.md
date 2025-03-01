# Adobe Audience Manager event reference

## Events handled

The following events are handled by the Audience Manager extension:

### Audience Manager content request

This event updates the profile for Audience Manager and is generated when the `audienceSignalWithData` API is called to send content to Audience Manager.

#### Event details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| `com.adobe.eventType.audienceManager` | `com.adobe.eventSource.requestContent` | Yes | ​[Audience Manager Content Response](#audience-manager-content-response)​ |

#### Data payload definition

The following lists the key-value pairs in this event:

| **Key or Key Type** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| `aamtraits` | String Map | No | The data payload contains the traits (key-value pairs) that were sent by the customer. |

### Audience Manager identity request

This event is a request to retrieve the visitor profile from Audience Manager and is generated when the parent application requests an audience visitor profile by using `audienceGetVisitorProfile`.

#### Event details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| `com.adobe.eventType.audienceManager` | `com.adobe.eventSource.requestIdentity` | Yes | ​[Audience Manager identity response](#audience-manager-identity-response)​ |

#### Data payload definition

There are no key-value pair for this event.

### Audience Manager reset request

This event clears the Audience Manager profile on the device and is generated when the `audienceReset` API is called to clear the Audience Manager profile.

#### Event details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| `com.adobe.eventType.audienceManager` | `com.adobe.eventSource.requestReset` | No | N/A |

#### Data payload definition

There are no key-value pairs for this event.

#### Hub shared state

Audience Manager listens for the configuration shared state events. For more information about shared state events, see the [shared states and events guide](../building-mobile-extensions/shared-states-and-events.md).

### Configuration response content

The Audience Manager extension listens for configuration content response events to detect whether the privacy status was changed or the audience configuration was updated.

For more information about the this event, see the configuration response content section of the [Adobe Analytics event reference](../adobe-analytics/event-reference.md#configuration-response-content)​.

### Lifecycle response content

This event is generated when there is a lifecycle session update such as a launch event or upgrade. The Audience Manager extension listens for the event and sends a new signal to Audience Manager with the lifecycle context data.

For more information about the this event, see the lifecycle response content section of the [Adobe Analytics event reference](../adobe-analytics/event-reference.md#lifecycle-response-content).

### Analytics response content

Audience Manager listens for Adobe Analytics response events, which are sent when audience forwarding is enabled, processes the events, and extracts the destinations where the new signals will be sent.

For more information about this event, see the Analytics response content section of the [Adobe Analytics event reference](../adobe-analytics/event-reference.md#analytics-response-content).

## Events dispatched

The following events are dispatched by the Audience Manager extension:

### Audience Manager content response

This event delivers the Audience Manager profile to the following:

* The original requester.
* A module that might be listening for updates.

The event is generated when a request is made to:

* Update the Audience Manager profile.
* Retrieve the current Audience Manager profile.

#### Event details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| `com.adobe.eventType.audienceManager` | `com.adobe.eventSource.responseContent` | Yes | ​[Audience Manager Content Request](#audience-manager-content-request)​ |

#### Data payload definition

The following lists the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| `aamprofile` | String Map | Yes | The data payload contains the customer key value pairs. The data payload is populated using the CV and CN values in the Audience Manager Stuff array. |

### Audience Manager identity response

This event delivers the Audience Manager profile to:

* The original requester
* Any module that might be listening for updates

The event is generated when a request is made to update the Audience manager profile.

#### Event details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| `com.adobe.eventType.audienceManager` | `com.adobe.eventSource.responseIdentity` | Yes | ​[Audience Manager identity request](#audience-manager-identity-request)​ |

#### Data payload definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| `aamprofile` | String Map | No | Audience Manager Visitor Profile |

## Shared states

`MODULE_NAME`: `com.adobe.module.audience`

The shared state for this module is updated in the following scenarios:

* **At Initialization**: After the module is initialized, it updates the shared state by reading the previously set value from persistence.
* **With Audience Manager API calls**: The shared stare is updated when the `submitsignal` API is called.

| Key | Type | Description |
| :--- | :--- | :--- |
| `uuid` | String | The UUID assigned by the Audience server. |
| `aamprofile` | Dictionary/Map | The matching visitor profile segments associated with the user. |

