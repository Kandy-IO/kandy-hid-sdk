kandy-hid exports a number of constants as a single object called CONSTANTS.

```
import { CONSTANTS } from '@distant/kandy-hid/constants/constants';
```
```
CONSTANTS: {
    "DEVICE_OPERATIONS": {
        "CALL_ACCEPT": "call_accept",
        "CALL_END": "call_end",
        "CALL_FAILURE_FINISH": "call_failure_finish",
        "CALL_FAILURE": "call_failure",
        "CALL_HOLD": "call_hold",
        "CALL_MUTE": "call_mute",
        "CALL_REJECT": "call_reject",
        "CALL_RESUME": "call_resume",
        "CALL_START": "call_start",
        "CALL_SWAP": "call_swap",
        "CALL_UNMUTE": "call_unmute",
        "CALLS_ON_HOLD": "calls_on_hold",
        "CHANNEL_ERROR": "channel_error",
        "DEVICE_CLOSE": "close",
        "DEVICE_ERROR": "error",
        "OFFHOOK": "offhook",
        "ONHOOK": "onhook",
        "RESET": "reset",
        "START_RINGING": "start_ringing",
        "STOP_RINGING": "stop_ringing"
    },
    "DEVICE_TYPES": {
        "MICROPHONE": "microphone",
        "SPEAKERS": "speakers",
        "ALERT_SPEAKERS": "alert_speakers"
    },
    "MODES": {
        "VDI": "VDI",
        "DESKTOP": "desktop"
    },
    "ACTIONS": {
        "ALLOW_HID_DEVICE_OPENS": "allowHIDDeviceOpens",
        "INVOKE_HID_FUNCTION": "invokeHIDFunction",
        "IS_SUPPORTED_DEVICE": "isSupportedDevice",
        "SELECT_HID_DEVICE": "selectHIDDevice",
        "UPDATE_SUPPORTED_DEVICES": "updateSupportedDevices"
    }
}
```
