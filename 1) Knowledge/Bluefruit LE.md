[Adafruit Feather M0 Bluefruit LE](https://learn.adafruit.com/adafruit-feather-m0-bluefruit-le)

Battery: Red = left, black = right

[Adafruit Feather M0 — PlatformIO 5.1.1a1 documentation](https://docs.platformio.org/en/latest/boards/atmelsam/adafruit_feather_m0.html?utm_medium=piohome&utm_source=platformio)

## Ack! I "did something" and now when I plug in the Feather, it doesn't show up as a device anymore so I cant upload to it or fix it...

No problem! You can 'repair' a bad code upload easily. Note that this can happen if you set a watchdog timer or sleep mode that stops USB, or any sketch that 'crashes' your Feather

1. Turn on verbose upload in the Arduino IDE preferences
2. Plug in feather 32u4/M0, it won't show up as a COM/serial port that's ok
3. Open up the Blink example (Examples->Basics->Blink)
4. Select the correct board in the Tools menu, e.g. Feather 32u4 or Feather M0 (check

   your board to make sure you have the right one selected!)

5. Compile it (make sure that works)
6. Click Upload to attempt to upload the code
7. The IDE will print out a bunch of COM Ports as it tries to upload. During this time,

   double-click the reset button, you'll see the red pulsing LED that tells you its now in

   bootloading mode

8. The Feather will show up as the Bootloader COM/Serial por



