+++
title = "Windows Mods & Programs"
date = "2022-07-20"
type = "post"
+++

## Posy's Mouse Cursor (default one)

Because the windows default one is crooked and does not look right, I changed my mouse cursor to this.
  
http://www.michieldb.nl/other/cursors/

---
## Turkish programmers layout (my own keyboard layout)

https://github.com/seyahdoo/turkish-programmer-keyboard-layout

---
## Autohotkey and Python scripts for stuff and Launchy or Steamdeck to launch them (no longer used)

https://github.com/seyahdoo/AHK
---
## Win 10 LTSB
A really stripped down and stable version of windows 10. 
It does not have most of the bloatware and it receives updates 1 year after the main channel.
Last time I have seen an LTSB iso image it had this fingerprint
```
name: en_windows_10_enterprise_ltsc_2019_x64_dvd_74865958.iso
size: 3878287360 bytes (3698 MiB)
sha1: 0B8476EFF31F957590ADE6FE671F16161037D3F6
```
---
## MPC-BE media player
Really basic media player. Successor for MPC-HC, basicly the same thing, but less dead.

https://sourceforge.net/projects/mpcbe/

---
## Irfan View photo & media viewer
Really basic photo viewer feels a lot like Win 7 photo viewer, no fuss, just viewing.

https://www.irfanview.com/64bit.htm

---
## Disable win 10 anti virus program 
Any type of antivirus is malware. Slows down the PC, it is not needed.

open gpedit.msc and appy below settings

```
Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Turn off Windows Defender Antivirus > Enabled
Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Real-time Protection > Turn on behavior monitoring > Disabled
Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Real-time Protection > Monitor file and program activity on your computer > Disabled
Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus > Real-time Protection > Turn on process scanning whenever real-time protection is enabled > Disabled
```
---
## Disable windows security notification app

```
open Task Manager
go to Startup
click Windows Secority notification icon
press Disable
```
---
## Uninstall internet explorer
Why do they even package it with the OS anyways? Remember to install Firefox before doing this. 

```
install firefox
go to "turn windows features on or off" using start menu search function
untick "Internet Explorer 11"
press ok, then restart
```

---
## Uninstall windows media player
Just dead weight.

```
go to "turn windows features on or off" using start menu search function
untick "Windows Media Player inside Media Features"
press ok, then restart
```
---
tosuncuk