# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 1.6.0 - 2021-01-29

### Removed
- The `updateSupportedDevices()` API, which was deprecated in version 1.3.1

### Added
- Ability to use the SDK in a Citrix VDI Windows environment
- Formal support for the Jabra Speak 750 in a VDI Windows environment

## 1.5.0 - 2020-05-15

### Added
- The ability to answer a call from a HID device while it is already active on a call
- The ability to swap between an active and held call from a HID device

### Fixed
- In Desktop (non-Citrix/VDI), device loss (disconnect / power loss) detection and handling has been improved

## 1.4.0 - 2020-03-20

### Added
- More robust messaging protocol between the Kandy HID Driver and Kandy HID SDK
- When used in Citrix VDI, the Kandy HID SDK is backwards compatible with certain previous versions of Kandy HID Driver for VDI see Backwards Compatibility in [README](./README.md)

## 1.3.1 - 2020-01-31

### Added
- In Citrix VDI, filtering of known / supported devices has been removed, meaning that kandy-hid will attempt to manage any HID-compatible device selected by the user <sup>1</sup>
- In Desktop, the ability to use the Jabra Evolve 80 and Jabra Speak 750 has been added <sup>1</sup>
- The ability to hold/resume an active call from a HID device is added for VDI mode (it was previously supported only for Desktop) <sup>2</sup>
- The ability to reject an incoming call from a HID device while on an active call is added <sup>2</sup>
- A new API is introduced - `isSupportedDevice()`; see usage details in [README](./README.md)

1- **NOTE that formal support is limited to the devices listed in the table in the [README](./README.md)**. Other devices (including the Speak 750 and Evolve 80) should be considered unsupported and used on a trial / evaluation basis only.<br>
2- The way that these features are invoked by the user aligns to each Jabra device's User Manual. See Use Cases in the README for details<br>

### Changed
- after rejecting a call, the device is returned to its previous state, e.g. on another call, on hold, muted, etc. Previously the device would return to idle state after rejecting a call regardless of its previous state
- KandyHID is renamed kandy-hid
- kandy-hid is now delivered as a .tgz file within the Distant set of tools and utilities
- This requires changes to how kandy-hid is added to your app packaging:
  - it should now be added to your package.json as<br>`file:<path_to_file>/distant-kandy-hid-v1.0.0.tgz`
  - it should be imported or required within the app as<br>`@distant/kandy-hid`

### Removed
- the SUPPORTED_DEVICE_LABELS object is no longer exported as a constant

### Deprecated
- it's no longer necessary to call `updateSupportedDevices()` from the app; it's called as necessary during device selection. There is no adverse effect to calling it, it's simply no longer necessary. The API should be considered as deprecated and will likely be removed in a future version

## 1.2.1 - 2020-01-10

### Added
- Support for Jabra Engage 65 firmware 3.4.1

## 1.2.0 - 2019-11-04

### Added
- One of each supported type of HID device may now be connected to a Thin Client simultaneously; the limitation that the same device must be selected for microphone, speakers and alert speakers remains
- Support is added for Jabra Speak 710 and Engage 50 in Desktop (non-VDI) mode
- The setLogger() API is introduced to allow a custom logger to be passed in for use

### Fixed
- An intermittent issue relating to the PRO 9450 mute state not being properly reflected in the app in Desktop mode is resolved

## 1.1.0 - 2019-08-16

### Added
- Support for the Jabra Speak 710 in VDI mode

### Changed
- When DEVICE_ERROR is received by your app for a device power loss or physical disconnection, it is no longer necessary to send a 'device_close' request to kandy-hid; kandy-hid will automatically close the device on error.
- `electron-log` dependency is removed. All logs are regular `console.log` or `console.error`.
- CHANNEL_ERROR will be raised on the `HIDFunctionRequest` event in case of a communication error over the virtual channel
- KANDYHID_ACTIONS are defined as constants and available for use in your app
- An intermittent issue relating to Engage 50 mute state not being properly reflected in the app is resolved

<!-- changelog possible fields:
### Added
### Changed
### Removed
### Deprecated
### Fixed
### Security
>