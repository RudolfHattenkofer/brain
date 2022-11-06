## Setup

The whole component is a simple shield that can just be plugged into the Raspberry GPIO Headers.

- `raspi-config`
- Enable SPI
- Reboot
- Ensure running `lsmod | grep spi`

## Basics

Supplier: [PN532 NFC HAT - Waveshare Wiki](https://www.waveshare.com/wiki/PN532_NFC_HAT)

[https://www.waveshare.com/pn532-nfc-hat.htm](https://www.waveshare.com/pn532-nfc-hat.htm)

## Code

```swift
pip3 install adafruit-circuitpython-pn532
```

```swift
import board
import busio
from digitalio import DigitalInOut

from adafruit_pn532.spi import PN532_SPI

spi = busio.SPI(board.SCK, board.MOSI, board.MISO)
cs_pin = DigitalInOut(board.D4)
pn532 = PN532_SPI(spi, cs_pin, debug=False)

ic, ver, rev, support = pn532.firmware_version
print("Found PN532 with firmware version: {0}.{1}".format(ver, rev))

# Configure PN532 to communicate with MiFare cards
pn532.SAM_configuration()

uuids = []
print("Waiting for RFID/NFC card...")
while True:
    # Check if a card is available to read
    uid = pn532.read_passive_target(timeout=0.5)
    # print(".", end="")

    # Try again if no card is available.
    if uid is None:
        continue

    if uid in uuids:
      continue
    else:
      uuids.append(uid)

      print("Found card with UID:", end="")

      for i in uid:
        print(hex(i)[2:], end="")

      print()
```



