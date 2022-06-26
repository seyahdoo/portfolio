+++
title = "Installing QMK on Keychron k3v2 RGB edition"
date = "2022-06-26"
keywords = ["Keychron", "k3v2", "k3", "rgb", "qmk", "sonixqmk"]
+++

### Disclaimer:
- Bluetooth connectivity will not work after this modification
- After I did this modification my keyboard is sometimes not working after plugging in.
I have to plug in several times to make it work sometimes.

### How to do it:

- Using this guide; https://sonixqmk.github.io//SonixDocs/install/
  - Setup QMK environment with Sonix QMK repo 
  - Download "Sonix Keyboard Flasher"
  - Compile QMK Sonix fimware; 
  - This is command for Keychron k3v2 with RGB 
  ```
  qmk compile -kb keychron/k3/rgb/optical_iso -km via_iso
  ```
  - And here is how my output looks like on a successfull run
  
  ```
   Ψ Compiling keymap with make --jobs=1 keychron/k3/rgb/optical_iso:via_iso                                                                                                                    
   QMK Firmware 0.7.101                                                                                      
   Making keychron/k3/rgb/optical_iso with keymap via_iso                                                                                                                                                           
   arm-none-eabi-gcc.exe (GCC) 10.1.0                                                                        
   Copyright (C) 2020 Free Software Foundation, Inc.                                                         
   This is free software; see the source for copying conditions.  There is NO                                
   warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.                                                                                                                                      
   Size before:                                                                                              
      text    data     bss     dec     hex filename                                                          
         0   53754       0   53754    d1fa .build/keychron_k3_rgb_optical_iso_via_iso.hex                                                                                                                     
   Compiling: keyboards/keychron/k3/keymaps/via_iso/keymap.c                                           [OK]  
   Compiling: quantum/via.c                                                                            [OK]  
   Linking: .build/keychron_k3_rgb_optical_iso_via_iso.elf                                             [OK]  
   Creating binary load file for flashing: .build/keychron_k3_rgb_optical_iso_via_iso.bin              [OK]  
   Creating load file for flashing: .build/keychron_k3_rgb_optical_iso_via_iso.hex                     [OK]                                                                                                        
   Size after:                                                                                               
      text    data     bss     dec     hex filename                                                          
         0   53754       0   53754    d1fa .build/keychron_k3_rgb_optical_iso_via_iso.hex                                                                                                                     
   Copying keychron_k3_rgb_optical_iso_via_iso.bin to qmk_firmware folder                              [OK]  
   (Firmware size check does not yet support SN32F248BF; skipping)                                           
   ```
  - Binary is at your home "qmk_firmware" folder
  
- Disassemble the keyboard
- Switch to cable mode
- Uplug keyboard
- While shorting boot Pins; Plug the keyboard to PC
- Keyboard should be unresponsive and "Sonix Keyboard Flasher" app should see the flashable chip
- Set settings: device = SN32F24x, qmk offset = 0x00
- Then Flash QMK with the binary that you made in the compiling stage.
- You dont need to disassemble keyboard to get to bootloader mode anymode. Just press Fn+Esc
