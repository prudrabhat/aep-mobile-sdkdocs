import AddAnalyticsIos from './tabs/index/add-analytics/ios.md'
import AddAnalyticsAndroid from './tabs/index/add-analytics/android.md'
import AddAnalyticsReactNative from './tabs/index/add-analytics/react-native.md'
import RegisterMediaIos from './tabs/index/register-media/ios.md'
import RegisterMediaAndroid from './tabs/index/register-media/android.md'
import RegisterMediaReactNative from './tabs/index/register-media/react-native.md'

# Adobe Analytics - Media Analytics for Audio and Video

<InlineAlert variant="warning" slots="text"/>

This extension requires the [Adobe Analytics for Media](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html) add-on SKU. To learn more, contact your Adobe Customer Success Manager.

## Configure Media Analytics extension in the Data Collection UI

1. In the Data Collection UI, select the **Extensions** tab.
2. On the **Catalog** tab, locate the **Adobe Media Analytics for Audio and Video** extension, and select **Install**.
3. Type the extension settings. For more information, see [Configure Media Analytics Extension](./#configure-media-analytics-extension).
4. Select **Save**.
5. Follow the publishing process to update your SDK configuration.

## Configure the Media Analytics extension

<InlineAlert variant="info" slots="text"/>

If you update the Adobe Media Analytics for Audio and Video launch extension to v2.x in your launch property, you must make sure to update and use AEP SDK Media extension v2.0.0 and higher.

![Adobe Media Analytics Extension Configuration](./images/index/configuration.png)

To configure the Media Analytics extension, complete the following steps:

### Collection API Server

Type the name of the media collection API server. This is the server where the downloaded media tracking data is sent. Important: You need to contact your Adobe account representative for this information.

### Channel

Type the channel name property.

### Player name

Type the name of the media player in use (for example, _AVPlayer_, _Native Player_, or _Custom Player_).

### Application version

Type the version of the media player application/SDK.

<InlineAlert variant="info" slots="text"/>

Legacy settings should not be configured for Media Extension v2.x and higher. Those settings are only for backwards compatibility.

If you are using Media Extension v1.x, then go to Legacy settings section 1. Enable the `Use Tracking Server` checkbox. 2. In **Tracking Server**, Type the name of the tracking server to which all media tracking data should be sent.

## Add Media Analytics to your app

<InlineAlert variant="info" slots="text"/>

This extension requires the [Adobe Analytics extension](../adobe-analytics/index.md). You must add the Analytics extension to your Launch property and make sure the extension is correctly configured.

<TabsBlock orientation="horizontal" slots="heading, content" repeat="3"/>

Android

<AddAnalyticsAndroid/>

iOS

<AddAnalyticsIos/>

React Native

<AddAnalyticsReactNative/>

## Register Media with Mobile Core

<TabsBlock orientation="horizontal" slots="heading, content" repeat="3"/>

Android

<RegisterMediaAndroid/>

iOS

<RegisterMediaIos/>

React Native

<RegisterMediaReactNative/>

## Configuration keys

FIX LINK

To update your SDK configuration programmatically, use the following information to change your Media configuration values. For more information, see [Configuration API reference](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/configuration/configuration-api-reference).

| Key | Required | Description | Data Type |
| :--- | :--- | :--- | :--- |
| `media.collectionServer` | Yes | Media Collection Server endpoint to which all the media tracking data is sent. For more information, see [Collection Server](./#collection-api-server). | String |
| `media.channel` | No | Channel name. For more information, see [Channel](./#channel). | String |
| `media.playerName` | No | Name of the media player in use, i.e., "AVPlayer", "HTML5 Player", "My Custom Player". For more information, see [Player Name](./#player-name). | String |
| `media.appVersion` | No | Version of the media player app/SDK. For more information, see [Application Version](./#application-version). | String |

## Platform Support

| Platform | Support Status |
| :--- | :--- |
| Android | Supported |
| Apple iOS​ | Supported |
| React Native (iOS & Android) | Supported |
