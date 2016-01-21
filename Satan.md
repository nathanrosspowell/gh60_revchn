This is a quick guide to changing the keymap on the GH60 "Satan" or RevCHN. Note that the Satan is NOT a true GH60, and using the GH60 with the normal TMK would not work.

Note that installing dependencies or compiling TMK is not a part of the scope of this document. If you have problems with this part, seek help elsewhere.
Not also that these instructions are written for Linux and Mac. If you're using windows, just use the Command Prompt for the git commands, and Windows Explorer to move and delete files.

1. Dependencies.
  1. Download and install GIT: https://git-scm.com/downloads
  2. Download and install the dependencies for compiling TMK: https://github.com/tmk/tmk_keyboard/blob/core/doc/build.md (Point 1 only)
  3. Using git, download the TKG toolkit. https://github.com/kairyu/tkg-toolkit ```git clone git@github.com:kairyu/tkg-toolkit.git tkg```
  4. Still using git, download Kairyu's fork of TMK. https://github.com/kairyu/tmk_keyboard_custom ```git@github.com:kairyu/tmk_keyboard_custom.git tmk```
  (Note that I've renamed the folders and that they're named quite similarly. Take care of which you're working in in order not to get things wrong.)
  6. Update the submodules for TMK. Do this from inside the tmk folder:
    ```git submodule update```
2. Compile the keymap
  1. First, you need to actually write your keymap. This is explained here: https://github.com/tmk/tmk_keyboard/blob/core/doc/keymap.md
  2. Go to tmk/keyboard/gh60
  2. Put the keymap file there (should be called keymap_SOMETHING.c, eg, keymap_custom.c) 
  2. To compile the keymap, run this command, substituting 'custom' with whatever your file is called.
    ```make KEYBOARD=custom```
  5. Wait. At the end there should be lots of new files there. We only need one. Copy the file ```gh60_lufa.hex``` somewhere safe for now. Keep backups of this, it's your new firmware.
3. Flash the firmware 
  1. Now go to the TKG folder. Enter either the tkg/linux or the tkg/windows folder depending on your OS. 
  2. Run the setup script. Use these options:
    1. 2 - GH60 RevCHN
    2. y - .. Yes...
    3. 1 - Default
    4. 1 - atmel_dfu (Yes, I know the file says lufa. That doesn't matter!)
  3. Cheat. 
    1. Rename tkg/common/firmware/gh60-revchn.hex to gh60-revchn.original.hex
    2. Copy your firmware from one of your several backups to the same folder, and rename it gh60-revchn.hex
    3. Back in the windows/linux folder, run reflash. Press enter, and when it says "Waiting for bootloader", press the little button on the bottom of the PCB. 
    4. You are now finished!
  5. Enjoy!!!!
  6. If you aren't happy with the keymap, and want to make a new one, remember to  ```make clean``` before you recompile.