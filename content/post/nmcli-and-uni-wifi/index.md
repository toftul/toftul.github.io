---
title: "nmcli connect to university wifi (WPA2-Enterprise)"
description:
date: 2024-03-03T17:28:32+11:00
image:
math: true
license:
hidden: false
comments: true
draft: false
tags: ["linux", "raspberrypi", "cli"]
categories: ["linux"]
---


## Why

I needed to connect my Raspberry Pi to an university Wi-Fi, which has WPA2-Enterprise encryption (require login and pass). All straight forward attempt fail since `nmcli` cannot configure it automatically. Something like
```shell
nmcli device wifi connect ANU-Secure
```
would give an error
```shell
Error: Failed to add/activate new connection: Failed to determine AP security information
```

## How

Create a connection
```shell
sudo nmcli con add type wifi ifname wlan0 con-name UNI-WIFI ssid WIFISSID
```
Now edit it
```shell
sudo nmcli connection edit UNI-WIFI
```

You will get into the nmcli console. Do the following settings:
```
set 802-1x.eap peap    
set 802-1x.phase2-auth mschapv2    
set 802-1x.identity _yourUsername_    
set 802-1x.password _yourPassword_   
set wifi-sec.key-mgmt wpa-eap
save
activate
```

Press `ctrl`-`d` to exit nmcli interface. You're done! It should autoconnect after reboot. If not change this setting explicitly by
```shell
sudo nmcli con mod ens3 connection.autoconnect yes
```

Sources:
- https://www.reddit.com/r/archlinux/comments/pb3r0f/cannot_connect_to_college_wifi_using/
- https://docs.rockylinux.org/gemstones/nmcli/



