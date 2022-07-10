+++
title = "Installing QMK on Keychron k3v2 RGB with optical switches"
date = "2022-06-28"
tags = ["Keychron", "k3v2", "k3", "rgb", "qmk", "sonixqmk"]
type = "post"
+++

### Disclaimer:
- Bluetooth connectivity will not work after this modification
- On my system, when you first plug the usb cable, it almost never connects at the first time. 
So I added `eeconfig_init();` on `void keyboard_post_init_user(void)` function. It works after I have added that.

### How to do it:

- Using this guide; https://sonixqmk.github.io//SonixDocs/install/
  - Setup QMK environment with Sonix QMK repo 
  - Apply config and keymap files
  - Download "Sonix Keyboard Flasher"
  - Compile QMK Sonix fimware with this command -> `qmk compile -kb keychron/k3/rgb/optical_iso -km iso`
  - Binary is at your home "qmk_firmware" folder and named with ".bin" extension
  
- Disassemble the keyboard
- Switch to cable mode
- Uplug keyboard
- While shorting boot Pins; Plug the keyboard to PC
- Keyboard should be unresponsive and "Sonix Keyboard Flasher" app should see the flashable chip
- Set settings: device = SN32F24x, qmk offset = 0x00
- Then Flash QMK with the binary that you made in the compiling stage.
- You dont need to disassemble keyboard to get to bootloader mode anymode. Just press Fn+Esc


---
My Compiled Firmware: [Download Firmware](/files/keychron_k3/keychron_k3_rgb_optical_iso_iso.bin)

My Keymap: [Download Keymap](/files/keychron_k3/keymap.c)

My Config: [Download Config](/files/keychron_k3/config.h)

My CI for building firmware: [Firmware CI Repo](https://github.com/seyahdoo/k3-v2-optical-qmk)
