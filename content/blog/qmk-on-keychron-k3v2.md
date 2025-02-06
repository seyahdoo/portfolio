+++
title = "Installing QMK on Keychron k3v2 RGB with optical switches"
date = "2022-06-28"
type = "post"
+++

### Disclaimer:
- Bluetooth connectivity will not work after this modification
- On my system, when you first plug the usb cable, it almost never connects at the first time; 
I've added `#define NO_USB_STARTUP_CHECK = yes` to the `config.h` to fix it.
I'm really not sure why this fixes it but I've got the idea from here. > https://github.com/qmk/qmk_firmware/issues/5585

### How to do it:

- Using this guide; https://sonixqmk.github.io//SonixDocs/install/
  - Setup QMK environment with Sonix QMK repo 
  - Apply config and keymap files
  - Download "Sonix Keyboard Flasher"
  - Compile QMK Sonix fimware with this command -> `qmk compile -kb keychron/k3/rgb/optical_iso -km iso`
  - Binary is at your home "qmk_firmware" folder and named with ".bin" extension
  
- Disassemble the keyboard (you dont have to disassemble everything, just remove the keycaps next to the screws)
- Switch to cable mode
- Uplug keyboard
- While shorting boot Pins; Plug the keyboard to PC
- Keyboard should be unresponsive and "Sonix Keyboard Flasher" app should see the flashable chip
- Set settings: device = SN32F24x, qmk offset = 0x00
- Then Flash QMK with the binary that you made in the compiling stage.
- You dont need to disassemble keyboard to get to bootloader mode anymore, just press Fn+Esc


---
My Compiled Firmware: [Download Firmware](https://github.com/seyahdoo/k3-v2-optical-qmk/releases/latest/download/keychron_k3_rgb_optical_iso_iso_seyahdoo.bin)

Source Code: [Firmware CI Repo](https://github.com/seyahdoo/k3-v2-optical-qmk)
