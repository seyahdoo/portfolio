+++
title = "Pixel 5 Imei Repair Guide"
date = "2023-09-16"
type = "post"
+++


### The Reason

The info on how to repair imei on pixel 5 is quite sparse and I needed a day of hacking around to actually do it.
Im writing this guide to maybe help another soul that is on this same journey for some reason.
Hopefully this helps. Have a great day fella <3 


### How To do It

```
- unlock bootloader (this will wipe the device, make sure you have backup)
- downgrade the system to earliest possible firmware (redfin-rd1a.200810.020.a1-factory-7ac5ecfc)
- go to bootloader mode
- download latest twrp
- boot to latest twrp (you dont need to insall it)

# backup modem partitions
adb shell mkdir /tmp/efs-backup/
adb shell dd if=/dev/block/bootdevice/by-name/modemst1 of=/tmp/efs-backup/modemst1.img
adb shell dd if=/dev/block/bootdevice/by-name/modemst2 of=/tmp/efs-backup/modemst2.img
adb shell dd if=/dev/block/bootdevice/by-name/fsg of=/tmp/efs-backup/fsg.img
adb shell dd if=/dev/block/bootdevice/by-name/fsc of=/tmp/efs-backup/fsc.img
adb pull /tmp/efs-backup
adb reboot

- root the device

# put modem to diag mode
adb shell
su
resetprop ro.bootmode usbradio
resetprop ro.build.type userdebug
setprop sys.usb.config diag,diag_mdm,adb
diag_mdlog
- Ctrl + C if and when it hangs or loops
- after it finishes change from charging mode to file transfer mode

# xqcn backup
- Run QPST Configuration
- Start Clients > Software Download
- Backup > Select Port > Browse for file to create > Start
this will create a .xqcn file, this is human editable, backup the original version of this file.


# delete modem data 
(this will disable the readonly protection on modem data) 
(make sure you have the qcn backup and modem partition backup before doing this. 
otherwise you may not be able to recover to original)

adb reboot bootloader
boot to latest twrp (you dont need to insall it)
adb shell
dd if=/dev/zero of=/dev/block/bootdevice/by-name/modemst1
dd if=/dev/zero of=/dev/block/bootdevice/by-name/modemst2
dd if=/dev/zero of=/dev/block/bootdevice/by-name/fsg
dd if=/dev/zero of=/dev/block/bootdevice/by-name/fsc
reboot

# put modem to diag mode
adb shell
su
resetprop ro.bootmode usbradio
resetprop ro.build.type userdebug
setprop sys.usb.config diag,diag_mdm,adb
diag_mdlog
- Ctrl + C if and when it hangs or loops
- after it finishes change from charging mode to file transfer mode

# edit the .xqcn file if you need to
the algorithm to change imei number to hex is as follows

08 (first number of imei)A (rest of the imei but the every two number is switched)

example conversion

123456789012345

    1 23 45 67 89 01 23 45

08 1A 32 54 76 98 10 32 54

find the imei on the file and replace if needed, dont forget to backup your original .xqcn file

# restore xqcn
Run QPST Configuration
Start Clients > Software Download
Restore > Select Port > Browse for the xqcn file > Lightly Spam Start Button
You might wanna restore multiple times (It might solve the imei not setting problem)
reboot phone

# done
at this time phone functions should work normally.
you might want to remove the root
you might want to upgrade the software to latest
factory resetting from the settings app does not ruin it
cant lock the bootloader again because that would ruin the modem mod

```


### Restoring To Original Modem Settings

```
boot to twrp

adb push efs-backup /tmp
adb shell dd if=/tmp/efs-backup/modemst1.img of=/dev/block/bootdevice/by-name/modemst1
adb shell dd if=/tmp/efs-backup/modemst2.img of=/dev/block/bootdevice/by-name/modemst2
adb shell dd if=/tmp/efs-backup/fsc.img of=/dev/block/bootdevice/by-name/fsc
adb shell dd if=/tmp/efs-backup/fsg.img of=/dev/block/bootdevice/by-name/fsg
adb reboot

```


### Useful Links
- https://twrp.me/
- https://flash.android.com/
- https://qpsttool.com
- https://github.com/topjohnwu/Magisk


### Thanks To

- [UFixer - for the method to go to modem diag mode](https://www.youtube.com/watch?v=YpG3o753D3A)
- [trzpro - for the efs backup code](https://www.youtube.com/watch?v=wSAGF066V1E)
- [hovatek - for the algorithm on how to convert imei to hex](https://www.hovatek.com/forum/thread-26051.html)
- [Alpha Tech Zone - for the guide](https://www.youtube.com/watch?v=jEYjuYR5EOg&ab_channel=AlphaTechZone)
- [uragiristereo - for the pretty comprehensive guide](https://gist.github.com/uragiristereo/7668e067e3b0525d6e4d4b12d9f71344)
- [Homeboy76 - for the amazing guide on how to root](https://forum.xda-developers.com/t/guide-root-pixel-5-with-magisk-unlock-bootloader-pass-safetynet-more.4187609/)
- [Luxferre - for the insight on how modem works](http://chronovir.us/2019/04/09/8110-pwned-once-again-but-this-is-just-the-sTARt/)
- [Ustabas Osman - for the insight on how modem works](https://www.androidbrick.com/qualcomm-snapdragon-imei-tamiri-ders-4-qualcomm-snapdragon-imei-repair/)
- [Chema_F - for the insight on how modem works](https://forum.xda-developers.com/t/guide-backup-edit-and-restore-qcn-fixing-lost-imei.4101611/)


### Insights That Are Not Related To The Guide

- most probably original imei data is on fsg.img file
- on some cases its a tar file or a linux file system (sadly its not for the pixel 5)
- FSG = Modem Storage "Golden Copy"


### Link Pool (some might contain viruses)

- https://developers.google.com/android/images
- https://flash.android.com/build/10316531?target=redfin-user&signed=true&wipe=true&forceFlash=true&lock=true
- https://forum.xda-developers.com/t/guide-root-pixel-5-with-magisk-unlock-bootloader-pass-safetynet-more.4187609/
- https://gist.github.com/uragiristereo/7668e067e3b0525d6e4d4b12d9f71344
- https://www.youtube.com/watch?v=YpG3o753D3A&ab_channel=UFixer
- https://www.youtube.com/watch?v=jEYjuYR5EOg&ab_channel=AlphaTechZone
- https://www.youtube.com/watch?v=-GEKDoshIHc&ab_channel=RomShillzz
- https://www.hovatek.com/forum/thread-26051.html
- https://forum.xda-developers.com/t/dev-info-imei-0.3806064/
- https://forum.xda-developers.com/t/guide-backup-edit-and-restore-qcn-fixing-lost-imei.4101611/
- https://groups.google.com/g/bananahackers/c/OCxhh7bb3-4?pli=1
- http://chronovir.us/2019/04/09/8110-pwned-once-again-but-this-is-just-the-sTARt/
- http://chronovir.us/2019/04/23/Either-Qual-or-Comm/
- https://github.com/openpst/qcdm
- https://www.androidbrick.com/qualcomm-snapdragon-imei-tamiri-ders-3-qualcomm-snapdragon-imei-repair/
- https://www.androidbrick.com/qualcomm-snapdragon-imei-tamiri-ders-4-qualcomm-snapdragon-imei-repair/


