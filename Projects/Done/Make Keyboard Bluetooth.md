[Convert mechanical keyboard to wireless](https://www.reddit.com/r/MechanicalKeyboards/comments/7t6dix/convert_mechanical_keyboard_to_wireless/)

[Convert Any USB Keyboard To Bluetooth](https://hackaday.com/2016/09/04/convert-any-usb-keyboard-to-bluetooth/)

[Adafruit Feather 32u4 Bluefruit LE](https://www.adafruit.com/product/2829)

[Adafruit Micro-Lipo Charger for LiPo/LiIon Batt w/MicroUSB Jack](https://www.adafruit.com/product/1904)

[Guide to USB-C Pinout and Features - Technical Articles](https://www.allaboutcircuits.com/technical-articles/introduction-to-usb-type-c-which-pins-power-delivery-data-transfer/)

[gdsports/ble-usb-devices](https://github.com/gdsports/ble-usb-devices)

- Get [library](https://github.com/gdsports/USB_Host_Library_SAMD) and add it via PlatformIO
- Get [code](https://github.com/gdsports/ble-usb-devices/tree/master/USBKbdBle) and place it in /src
- Get Adafruit BLE [library](https://learn.adafruit.com/adafruit-feather-m0-bluefruit-le/installing-ble-library) and place in /lib

We need this library?

[gdsports/USB_Host_Library_SAMD](https://github.com/gdsports/USB_Host_Library_SAMD)

Bought the wrong board… We need the M0 because the 32u4 cannot be a USB host.

Bluefruit LE

USB HID Media keys

## Further

hidboot.h line 374

The keyboard has two interfaces - #0 Boot and #1 HID. #1 contains the Consumer keys, which contains the media keys. We are currently only listening to interface #0, not the #1.

Number of total interfaces: 2

For consumer:

Interface #1 HID

Descriptor 1

For some fucked up reason I can’t seem to access the second interface from the Arduino… Ended up just reflashing the keyboard firmware and listen for F23 and F24 keys to send the signal over bluetooth… I mean that works too so whatever.



