[WiFi credentials](https://docs.google.com/spreadsheets/d/1fxOnDAjdgBHVEWAiKoMlgeWc3GfHEfS2byUZAF6_glQ/edit#gid=0)

[balena dashboard](https://dashboard.balena-cloud.com/login)

## Option 1

Directly configure in command line:

```swift
nmcli c edit resin-wifi-01
set 802-11-wireless.ssid Friends of RECUP
set 802-11-wireless-security.psk Mehrweg2019
save
Ctrl+D

# Persist & verify:
cat /etc/NetworkManager/system-connections/resin-wifi-01 > /mnt/boot/system-connections/resin-wifi-01

reboot
cat /etc/NetworkManager/system-connections/resin-wifi-01
```

## Option 2

[balena-io/wifi-connect - Libraries.io](https://libraries.io/github/balena-io/wifi-connect)

No WiFi and no network? Spawn AP, user logs in, enters credentials, application starts.



