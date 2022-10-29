[How to setup a Raspberry Pi RFID RC522 Chip - Pi My Life Up](https://pimylifeup.com/raspberry-pi-rfid-rc522/)

## Wiring

Also IRQ goes to pin 18 (GPIO24)

## Setup SPI

- `raspi-config`
- Enabled SPI
- Reboot
- Ensure running `lsmod | grep spi`

## Get ready

```swift
apt-get update
apt-get upgrade
apt-get install python3-dev python3-pip
```

## Code references

[MFRC522-python/mfrc522 at master · pimylifeup/MFRC522-python · GitHub](https://github.com/pimylifeup/MFRC522-python/tree/master/mfrc522)

Improved upon

[GitHub - mxgxw/MFRC522-python: A small class to interface with the NFC reader Module MFRC522](https://github.com/mxgxw/MFRC522-python)

Original

[MFRC522-python/MFRC522.py at master · tsndr/MFRC522-python · GitHub](https://github.com/tsndr/MFRC522-python/blob/master/MFRC522.py)

Another change? We’ll use this as the basis

[GitHub - lthiery/SPI-Py: Hardware SPI as a C Extension for Python](https://github.com/lthiery/SPI-Py)

Working spi lib for the above

## Setup

```swift
cd spi && python3 setup.py install
```



