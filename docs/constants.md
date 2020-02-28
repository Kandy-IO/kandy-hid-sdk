kandy-hid exports a number of constants as a single object called CONSTANTS.

```
import { CONSTANTS } from '@distant/kandy-hid/constants/constants';
```
```
CONSTANTS: {
    "DEVICE_OPERATIONS": {
        "RESET": "reset",
        "DEVICE_ERROR": "error",
        "DEVICE_CLOSE": "close",
        "CHANNEL_ERROR": "channel_error",
        "CALL_MUTE": "call_mute",
        "CALL_UNMUTE": "call_unmute",
        "START_RINGING": "start_ringing",
        "STOP_RINGING": "stop_ringing",
        "CALL_HOLD": "call_hold",
        "CALL_RESUME": "call_resume",
        "CALL_ACCEPT": "call_accept",
        "CALL_START": "call_start",
        "CALL_REJECT": "call_reject",
        "CALL_END": "call_end",
        "CALL_FAILURE": "call_failure",
        "CALL_FAILURE_FINISH": "call_failure_finish",
        "OFFHOOK": "offhook",
        "ONHOOK": "onhook"
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
        "UPDATE_SUPPORTED_DEVICES": "updateSupportedDevices",
        "SELECT_HID_DEVICE": "selectHIDDevice",
        "INVOKE_HID_FUNCTION": "invokeHIDFunction"
    }
}
```
