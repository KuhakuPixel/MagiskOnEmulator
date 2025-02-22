Install Magisk On Official Android Emulator
===========================================

Works on Android API 22 - 30,S (except 28)

0. Grab magisk.apk and put in this directory. If you're using ARM system image, replace `busybox` with `busybox_arm`.
1. For patching the ramdisk with magisk, your AVD must be already created
2. Make sure you backup the untouched `ramdisk.img` from `<sdk_home>/system-images/<platform>/*/ramdisk.img`. You will need it everytime you want to patch ramdisk with magisk (for the first time and also for subsequent magisk updates).
3. Clone this repository and copy the original `ramdisk.img` into the clone's folder.
4. Start the newly created AVD.
5. There are three ways to patch ramdisk:
  * Execute `patch.sh` or `patch.bat` to install Magisk (pre-downloaded) on the ramdisk.img 
  * Alternatively, you can execute `patch.sh canary` or `patch.bat canary` to install latest canary Magisk on the ramdisk.img. This requires AVD internet connectivity towards github.
***Note: If choosing to use 'patch.sh', you might need to run `dos2unix patch.sh` first so that the script has propper line ending. This is needed when using for example github for desktop, which changes line ending to CRLF instead of LF***
  * If you prefer patching by MagiskManager, execute `patch.sh manager` or `patch.bat manager`, it will create a fake `boot.img` on internal storage. We then launch MagiskManager and click `Install` and select `boot.img` to patch it. When finished,
execute `patch.sh pull` or `patch.bat pull` to get the patched ramdisk.img. This method is mainly for Released version of Magisk.

6. When finished, copy the patched `ramdisk.img` back to AVD directory.
7. Power off and restart (cold start) the emulator
8. Recommended: update magisk manager
9. Enjoy Magisk :)

Install Magisk On Android x86 Project on VirtualBox
===================================================

Only test on Android 8.1

0. Grab Magisk.zip (or Magisk.apk) and put in this directory.
1. Bring up Android system and establish adb connection.
2. Execute `prepare_image.sh` or `prepare_image.bat` to grab initrd.img and ramdisk.img on hard drive.
3. Execute `patch_vbox.sh` or `patch_vbox.bat` to patch initrd.img and ramdisk.img
4. Execute `install_vbox.sh` or `install_vbox.bat` to install patched images on hard drive.
5. Restart machine and enjoy Magisk :)

Reference: https://github.com/topjohnwu/Magisk/issues/2551#issuecomment-608998420

Sources
=======
busybox binary : https://github.com/Magisk-Modules-Repo/busybox-ndk

Notes
=====
| Emulator Version | command-line patch | manager patch
| ---- | ---- | ---- |
| Android S | Canary (22001) | Canary (22001, w/ built-in `su`) |
| Android 22 - 30 | Canary (22001) | 21.4 (w/ manager 8.0.7) |

MagiskManager 8.0.7: https://github.com/topjohnwu/Magisk/releases/download/manager-v8.0.7/MagiskManager-v8.0.7.apk

Magisk 21.4 channel url: https://bit.ly/304BAei (https://github.com/topjohnwu/magisk_files/blob/b0694fad863d3a15c6a2276b1061a280ece80ed7/stable.json)

Magisk 22001 Canary: https://github.com/topjohnwu/magisk_files/raw/c34d91edab45e140753e1256f2b694eed90d2dcc/app-debug.apk
