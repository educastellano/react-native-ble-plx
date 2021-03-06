**0.6.5**
- Fixed Null Pointer Exception when called `cancelDeviceConnection` on Android.
- Updated gradle version to be able to use latest Android Studio.
- Added Nullable and Nonnull annotations to Android implementation.

**0.6.4**
- Fail explicitly when carthage fails on postinstall.
- Added `mtu` property for `Device` object which allows you to get current BLE MTU of device.
- Added function `requestMTUForDevice` which allows to negotiate BLE MTU of device if it is possible.

**0.6.3**
- Updated RxBluetoothKit library to version 3.1.1
- Updated RxAndroidBle library to version 1.4.1
- Fixed NullPointerException when calling BLE operations without previous discovery.
- iOS emits values in `monitorCharacteristicForDevice` only when no reads are pending for specific characteristic.
  Previously when characteristic was notified and read operation was completed, characteristic value was received
  both in `readCharacteristicForDevice` and `monitorCharacteristicForDevice`. Now it will only be received in 
  `readCharacteristicForDevice` promise.

**0.6.2**
- Updated RxBluetoothKit library to version 3.0.14 to allow building library on XCode 9.
- Added new `localName` property to `Device` object, which is set when localName is available
  in device's advertisement data.
- Fixed build process on Windows.
- Fixed compatibility with RN 0.47
- Fixed bug when `onDeviceDisconnected` callback was not called on iOS when Bluetooth was 
  turned off on device.
- Updated library setup instructions.
- Added option to cache native libraries built by Carthage.

**0.6.1**
- Updated RxAndroidBle library to version 1.3.3 which fixes internal issues which may
  block execution of operation queue.
- Updated dev dependencies to fix latest Flowtype issues.
- Fixed bug when `restoreStateFunction` function could be called multiple times on iOS.

**0.6.0**
- Added basic API to support background mode. When BleManager is constructed you can pass
  `restoreStateIdentifier` and `restoreStateFunction` to `BleManagerOptions` object to
  enable support for background mode. More info about usage can be found in documentation.
- All subscriptions and promises are properly "Destroyed" when `destory()` function is called.
- Fixed bug on Android where notification messages could be duplicated or skipped.
- Updated RxAndroidBle to version 1.3
- Updated README file.
- Updated library logo

**0.5.0**
- Added new API for supporting unique Services and Characteristics:
  * `Characteristic.id`, `Service.id` fields which uniquely identify BLE objects.
  * All utility functions which don't require UUIDs as arguments are using
    internally `id` fields and therefore work faster and properly handle
    services/characteristics with same UUIDs. For example: `characteristic.read()`.
- New option to enable native modules' logging system via `bleManager.setLogLevel()` function.
- New function to read RSSI for connected devices: `bleManager.readRSSIForDevice()`.
- Updated RxBluetoothKit dependency to version 3.0.12
- Updated RxAndroidBle dependency to 1.2.2
- Added tests for JS API.
- Better Flow type checking and coverage.
- Documentation was moved to `./docs` folder and now is generated by documentation.js.
- Small fixes in examples.
- Updated installation steps.

**0.4.0**
- Device ID properties were renamed as they are not UUIDs on Android **(breaking change)**:
   * `Device.uuid` -> `Device.id`
   * `Service.deviceUUID` -> `Service.deviceID`, 
   * `Characteristic.deviceUUID` -> `Characteristic.deviceID`
- Changed signature of `onDeviceDisconnected`, as Device object is always available.
- Updated to Swift 3.0
- Updated to RxAndroidBle 1.1.0 and RxBluetoothKit 3.0.6
- Documentation was moved to `./doc` folder and now is generated by ESDoc.
- Fixed `state()` invalid return type. Implemented `state()` and `onStateChange()` for Android.
- Added optional parameter to `onStateChange()` function.
- Fixed `monitorCharacteristicForDevice()` for Android when characteristic accepts indications only.
- Updated `AndroidManifest.xml` configuration.