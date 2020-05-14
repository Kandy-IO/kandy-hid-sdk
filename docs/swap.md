# Call Swap

## Definition and Precondition
A "call swap" is the act of toggling between an active call and a held call. Therefore, the precondition exists that before a call swap can be performed, your app must be engaged on an active call and have at least one call on hold.

## Requirements
Be aware of the limitations described in [driver compatibility documentation](./compatibility.md).

## Performing a call swap
Performing a call swap from your application simply involves putting the active call on hold (sending kandy-hid a call hold request), and then immediately resuming a held call (sending kandy-hid a call resume action). This will in essence cause kandy-hid to perform a hookflash, causing the attached device to toggle between the active and held call.

It's important to note that in a WebRTC-only world, this has little meaning. You could perform a hold/resume in your app and never send kandy-hid anything, and the result would be the same. The idea that the managed device has a call on hold is meaningful only if physical telephone handsets or lines are connected to the HID device (as is possible with the Jabra Engage 65 and Jabra PRO 9450), in which case hookflash signals could be sent from the device to the telephony switch (PBX, etc) that manages calls. In order to work in this configuration, kandy-hid provides full call swap functionality.

Performing a call swap from a HID device involves the same user action as putting a call on hold or resuming a held call (typically a long-press on a single-buttoned device such as the Engage 50, or pressing the green Call button on a two-button device like the Jabra Speak 710). 

## Enabling Call Swap
The way that kandy-hid knows to interpret the hold/resume user action as the user's desire to perform a call swap, as opposed to a normal hold or resume, is determined by whether the preconditions are met or not. In other words, if the app and device are engaged on a call and there's a call on hold, kandy-hid will interpret the hold/resume physical action as the intention to swap calls, and send a 'call_swap' operation on the `HIDFunctionRequest()` event. If the preconditions are not met, the hold/resume physical action will simply be interepreted as hold or resume. **This means that when preconditions are met, an active call cannot be put on hold nor resumed from the device.**

It's important to note that before kandy-hid can correctly distinguish between the user's desire to hold/resume or swap calls, your app must inform kandy-hid when there are calls on hold, and when this condition clears. kandy-hid is aware of whether or not a managed device is engaged on a call, but it cannot know if your app has calls on hold, so it must be told. This is done by sending a new message type on the `invokeHIDOperation()` API, 'calls_on_hold'. It requires a boolean (true/false) parameter. Your app should call this API with `true` when calls are put on hold in your app, and `false` when there are no longer calls on hold in the app. This effectively enables and disables kandy-hid's call swap functionality. Since kandy-hid's internal 'calls_on_hold' value defaults to false, if it's never set to true by your app, kandy-hid will never signal a call swap and will always signal hold/resume.

### Usage
```
invokeHIDFunction('calls_on_hold', <boolean>)
```

### Examples

#### Keeping kandy-hid updated with held call information

```
const { invokeHIDFunction } = require('@distant/kandy-hid')

let lastState = false

setInterval(() => {
  const areCallsOnHold = Boolean( findHeldCalls() )

  if (areCallsOnHold !== lastState) {
    lastState = areCallsOnHold

    invokeHIDFunction('calls_on_hold', areCallsOnHold)
  }
}, 1000)
```

#### Handling the 'call_swap' event in the application
```
ipcRenderer.on('HIDFunctionRequest', (event, operation) => {
  switch (operation):
    case 'call_swap': {
      const activeCall = findActiveCall()
      const heldCalls = findHeldCalls()

      if (activeCall && heldCalls.length === 1) {
        holdCall(activeCall)
        resumeCall(heldCalls[0])
      }

      break
    }
}
```