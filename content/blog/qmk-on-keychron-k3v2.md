+++
title = "Installing QMK on Keychron k3v2 RGB with optical switches"
date = "2022-06-28"
keywords = ["Keychron", "k3v2", "k3", "rgb", "qmk", "sonixqmk"]
+++

### Disclaimer:
- Bluetooth connectivity will not work after this modification
- ~~After I did this modification my keyboard is sometimes not working after plugging in.
I have to plug in several times to make it work sometimes.~~ See the hack below.

### How to do it:

- Using this guide; https://sonixqmk.github.io//SonixDocs/install/
  - Setup QMK environment with Sonix QMK repo 
  - Download "Sonix Keyboard Flasher"
  - [HACK] Checkout chibios-contrib to commit d5e4fb2517b47a6a507fb765d3c78ea46b80f430 (this is a hack to solve the keyboard not working sometimes when you plug in)
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