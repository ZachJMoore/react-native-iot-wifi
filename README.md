# react-native-iot-wifi
Wifi configuration.
This library was written to config iot devices. With iOS 11 Apple introduced NEHotspotConfiguration class for wifi configuration. Library supports same functionality on ios and android.

## 1.0.1
* Bump handlebars from 4.0.12 to 4.1.2 in /example - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/15">PR #15</a>
* Bump js-yaml from 3.12.1 to 3.13.1 in /example - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/16">PR #16</a>
* Allow android Q to use wifi api for now - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/17">PR #17</a>
* Add podspec to support iOS auto-linking in RN >=0.60 - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/20">PR #20</a>
* fix null SSID crash - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/21">PR #21</a>
* iOS: added logic to trigger error if connection fails - <a href="https://github.com/tadasr/react-native-iot-wifi/pull/26">PR #26</a>

## 1.0.0
* Optional Force binding to a Wifi on both iOS and Android platforms
* Android: Better error handling
* Android: Detection for a system added config which cant be reused, removed or updated
* Android: Reliable polling for requested network connection for callbacks
* It does do a lot of other cleanup and re-use of code

## 0.4.5
Android:
* Makes the connect call asynchronous on Android
* Fails for Android Q as the API is deprecated

iOS:
* Fixes APIs on Simulator as it was behind a compile time macro
* Exposed and returns defaults for Simulator targets

## 0.3.0
* `connectSecure()` now works
* `getSSID()` should work on android

## iOS
> Important
> IOTWifi uses NEHotspotConfigurationManager. To use the NEHotspotConfigurationManager class, you must enable the Hotspot Configuration capability in [Xcode](http://help.apple.com/xcode/mac/current/#/dev88ff319e7).

1. Drang an drop `IOTWifi.xcodeproj` to your workspace
2. [Link target](https://help.apple.com/xcode/mac/current/#/dev51a648b07) to `libIOTWifi.a` library
3. [Link target](https://help.apple.com/xcode/mac/current/#/dev51a648b07) to `NetworkExtension.framework` framework
4. [Enable](http://help.apple.com/xcode/mac/current/#/dev88ff319e7) `Hotspot Configuration`
5. For iOS 12 [Enable](http://help.apple.com/xcode/mac/current/#/dev88ff319e7) `Access WiFi Information`

## android

## Usage

```javascript
import Wifi from "react-native-iot-wifi";

Wifi.isApiAvailable((available) => {
  console.log(available ? 'available' : 'failed');
});

Wifi.getSSID((SSID) => {
  console.log(SSID);
});

Wifi.connect("wifi-name", (error) => {
  console.log(error ? 'error: ' + error : 'connected to wifi-name');
});

Wifi.removeSSID("wifi-name", (error)=>{
  console.log(error ? 'error: ' + error : 'removed wifi-name');
});
```
