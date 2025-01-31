# XDM Experience Events

The Adobe Experience Platform Edge extension can send events that follow a previously defined XDM schema to Adobe Experience Edge Network. This extension automatically adds Identity information to each Experience event as described in this document.

## Event structure

<InlineAlert variant="info" slots="text"/>

This extension provides public APIs to build XDM Experience events; these events **should not** be confused with the events that are built by using the `Mobile Core` extension, as they are built based on XDM schemas.

An XDM Experience event has the following structure:

| Data | Required | Description |
| :--- | :------- | :--- |
| Timestamp | Yes | The auto populated timestamp when the Experience Platform event is sent to the AEP Edge mobile extension. |
| Event ID | Yes | Unique event identifier that is auto generated by the SDK. |
| Event type | Yes | The event type, for example `commerce:orderDetails`. Refer to [xdm:eventType Known Values](https://github.com/adobe/xdm/blob/master/docs/reference/classes/experienceevent.schema.md#xdmeventtype-known-values) for more examples. |
| XDM data | Yes | Data following the XDM schema that is defined in the Schema Editor. |
| Data | No | The JSON-formatted, free-form data that can be associated with an event. |
| Dataset ID | No | Using the AEP Edge extension, you can send data to multiple datasets based on your needs and configuration in Adobe Experience Platform. When sending an experience event and providing a dataset identifier, this identifier is used for redirecting the data to the specified AEP dataset instead of the default dataset set in the datastream configuration. |

## Identity

Here are the identity properties the AEP Edge mobile extension automatically adds to each Experience Event:

| Property | Description |
| :--- | :--- |
| ECID | The Experience Cloud Identifier (ECID)  that is generated by the Adobe Experiece Platform Mobile SDK is added to the Experience event's `XDM IdentityMap` . |

## Implementation Details

Implementation details are automatically collected by the Edge Network extension and are sent with every Experience Event. The implementation details format is defined in [XDM](https://github.com/adobe/xdm/blob/master/components/datatypes/industry-verticals/implementationdetails.schema.json).

| Property | Description |
| :--- | :--- |
| Version | The version string is a concatenation of the AEP Mobile Core extension version plus the Edge Network extension version. For example, `3.3.2+1.2.0`. |
| Name | The name is a unique URI identifier for the AEP Mobile SDK on each supported platform. For example, `https://ns.adobe.com/experience/mobilesdk/ios` for the Mobile SDK on iOS, or `https://ns.adobe.com/experience/mobilesdk/android/reactnative` for the Mobile SDK on Android using the React Native wrapper. |
| Environment | For a mobile application the environment is always `app`.|

If you would like to include this information in your dataset, add the "Implementation Details" field group to the schema tied to your dataset.

