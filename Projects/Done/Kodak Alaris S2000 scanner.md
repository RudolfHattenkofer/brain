Try to install Windows in emulated x64 processor.

Tool: UTM, Basis is QEMU. There is a nice tool called UTM that abstracts away a lot of the learning curve.
https://docs.getutm.app/guides/windows/

-> Really buggy and suuuuuuper slow, like ACTUALLY, really, completely unusable.

## Get this fking scanner working
https://docs.getutm.app/guides/ubuntu/
Then:
https://docs.getutm.app/guest-support/linux/

Get scanner drivers from: https://support.alarisworld.com/de-de/s2040-scanner#Software
Just open document scanner!

Alternatives:
gscan2pdf
XSANE

## Parallels
Password: adminadmin

## Separate Ubuntu on TK LES server

```
wget https://resources.kodakalaris.com/docimaging/drivers/Kodak_branded_drivers/s2000/LinuxSoftware_s2000_v8.2.x86_64.deb.tar.gz
tar -zxvf LinuxSoftware_s2000_v8.2.x86_64.deb.tar.gz
sudo apt-get install sane scanbd
sudo ./setup

sudo usermod -a -G saned rudolf
sudo usermod -a -G scanner rudolf
sudo usermod -a -G users rudolf

sudo apt purge ipp-usb
sudo apt-get install libusb-0.1-4
reboot
```

- https://cromwell-intl.com/open-source/xsane-invalid-argument.html
- https://wiki.ubuntuusers.de/SANE/
- https://forum.ubuntuusers.de/topic/leben-einhauchen-fuer-kodak-i2400-duplexscanne/

```
# List scanners
scanimage -L

# Test
scanimage --test
```


```
sudo apt purge ippusbxd kodak-s2000
wget http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.5_amd64.deb
sudo dpkg -i multiarch-support_2.27-3ubuntu1.5_amd64.deb
```