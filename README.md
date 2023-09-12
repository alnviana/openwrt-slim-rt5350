## Description
OpenWrt Barrier Breaker (v14.07) slimmed down to work on Ralink RT5350-based routers with 4MB Flash and 16MB RAM, to be used as Network Storage through Ethernet.

## Why?
I have a PlayStation 2 with OPL and I want to play games through Ethernet for best performance, but with someting simple and portable. I saw some people buying that kind of budget chinese devices to work as that, but when I bought and received a 4/16 device without SMB feature.
So, to take advantage of this, I decided to give a try.

## What was removed?
I tried to keep what is necessary to run Ethernet, USB, Storage and Samba, trying to remove/disable everything else:
- Kernel Printk
- Kernel Crashlog
- Kernel DebugFS
- Kernel Debug
- Kernel Info
- Kernel SysRQ
- Swap
- IPv6
- DNSMasq
- Firewall
- Mtd
- Opkg
- Iptables (IPv4/IPv6)
- NAT
- PPPoE
- WAN/WAN6
- USB 1.0/1.1
- Wireless Modules
- iw/iwinfo
- Crypto Modules (Wifi WPA AES)
- DHCP (IPv4/IPv6)
- Logs
- NTP
- Telnet
- Nmbd (Samba)
- Unused Ethernet ports (Reduces Energy Power consumption)

## What device is compatible?
I build OpenWrt with "Hame MPR-A1" target profile. I tested on a device named "HXT 3G Router", that have "Ralink RT5350F" and "L8-V8" written on the board.
I tried firmwares from others routers with this and some work, so I think that any Ralink RT5350-based router is compatible.
- A5-V11
- Hame MPR-A1
- Hame MPR-A2 (I think that is the same as A1, but 8/32)

## How to flash?
1. Before everything: Try at your own risk, I'm not responsible for anything.
2. Download the firmware and flash tool from Release Page.
3. Configure on ethernet adapter the static IP as "192.168.1.55" and mask as "255.255.255.0".
4. Connect router to ethernet.
5. Start the Router in Recovery Mode. (Usually you need hold reset button and turn on)
6. Open flash tool.
7. Select the downloaded firmware in "??Root_uImage". (Never touch "??UBoot"!)
8. Click the biggest button, the first one above all "..." buttons. (Everything will be disable)
9. After some seconds, the tool will do a chime sound. This means that is sending the firmware to router.
10. After one or two minutes, a warning with "Ok" will appear. Click that.
11. Another chime sound will happen, this means that the flashing process ended and you can close the program.
12. After a minute, you can try to ping "192.168.1.1". If you receive response, it's all right.

## How can I use that?
1. Connect a USB Storage with the first partition formated as EXT3 on Router's USB.
2. Try to access SMB Share "share" in the Router.
3. The default credencial is user "root" and password "password". (That is the same for SSH, if you need.)
4. If you can see the files inside USB Storage, it's all right. (It's read only)

PS: After flash, USB Storage usually doesn't work if was connect. If that happen, restart the router.
