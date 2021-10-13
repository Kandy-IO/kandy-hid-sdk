# Backwards Compatibility

When used in a Citrix VDI eLux environment, the Kandy HID SDK is backwards-compatible with the most recent and one (1) previous version of Kandy HID Driver for VDI (DLL) (official releases only). This is intended to allow Kandy HID Driver for VDI upgrades on the Thin Client installed-base to lag behind application updates.

## Kandy HID SDK and Kandy HID Driver for VDI Compatibility Matrix

| Kandy HID SDK Version | Delivery Date | Compatible Kandy HID Driver for VDI Version(s)<sup>*</sup>    | Comments      |
| :-------------------: | :-----------: | :-----------------------------------------------------------: | ------------- |
| 2.1.0                 | 2021-10-08    | 1.4.0, 1.1.0                                                  | See Note 2    |
| 2.0.0                 | 2021-07-30    | 1.4.0, 1.1.0                                                  | See Note 2    |
| 1.6.0                 | 2021-01-29    | 1.4.0, 1.1.0                                                  | See Note 2    |
| 1.5.0                 | 2020-05-15    | 1.4.0, 1.1.0                                                  | See Note 2    |
| 1.4.0                 | 2020-03-20    | 1.4.0, 1.1.0                                                  | See Note 1    |
| 1.3.1                 | 2020-01-31    | 1.3.1                                                         |               |
| 1.2.1                 | 2020-01-10    | 1.2.0, 1.2.1                                                  |               |
| 1.2.0                 | 2019-11-04    | 1.2.0, 1.2.1                                                  |               |
| 1.1.0                 | 2019-08-16    | 1.1.0                                                         |               |

<p style="text-align: center"><i>* If a Kandy HID SDK is being used with an older but still compatible version of Kandy HID Driver for VDI, any product limitations imposed by the older version of driver remain in effect unless otherwise specified.</i></p>

### Notes and Limitations

1- A limitation existed in Driver version 1.1 whereby handling of an incoming call while a HID device was engaged on a call was not deterministic and so it was recommended that HID devices not be instructed to 'start ringing' in that scenario.

As a result, it is not possible to use the new functionality in SDK version 1.4 to reject an incoming call while on a call if driver version 1.1 is being used.

2- Similar to Note 1, it is not possible to use the new functionality in SDK version 1.5 to answer an incoming call while on a call if driver version 1.1 is being used.

Another limitation that existed in Driver version 1.1 was that calls could only be put on hold or resumed from the application, not from a HID device. As a result, it is not possible to initiate a call swap from a HID device when using driver version 1.1. Initiating a call swap from the application works as expected.