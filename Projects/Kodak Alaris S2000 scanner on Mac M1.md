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
```

- https://cromwell-intl.com/open-source/xsane-invalid-argument.html


```
# List scanners
scanimage -L

# Test
scanimage --test
```