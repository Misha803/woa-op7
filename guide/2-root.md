<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Running Windows on the OnePlus 7 Pro / 7T Pro

## Rooting your device

### Prerequisites
- [`Magisk`](https://github.com/topjohnwu/Magisk/releases/latest)

- [`Android platform tools`](https://developer.android.com/studio/releases/platform-tools)

### Copying your boot image to Android
- Connect your phone to your computer (with USB debugging enabled).
- Click the prompt on your phone to allow your computer to access your phone's data. If no prompt appears, go to your notification panel and click the USB notification, then change the connection type to **transferring files**.
- Copy the **boot.img** file from the **platform-tools** folder into your internal storage.

#### Patching the boot image
- Download and install **Magisk**, then open it.
- Press **Install** > **Patch a file** and select the **boot.img** you just copied.
- Once the patching has finished, locate  **magisk_patched-28000_XXXX.img** in your **Downloads** folder and copy it into the **platform-tools** folder on your computer.

### Reboot to fastboot mode
```cmd
adb reboot bootloader
```

#### Flashing your rooted boot image
> Replace `path\to\magisk_patched.img` with the actual path of the image
```cmd
fastboot flash boot_a path\to\magisk_patched.img
```

### Reboot to Android
```cmd
fastboot reboot
```

#### Finishing setup
- Open the **Magisk** app again.
- Follow the instructions on the screen, and your device should reboot after a few seconds.

### Copying the rooted boot image
> After your device has booted back into Android
```cmd
adb shell "su -c cp /dev/block/by-name/boot$(getprop ro.boot.slot_suffix) /sdcard/rooted_boot.img" & adb pull /sdcard/rooted_boot.img
```
- A superuser request for Shell might appear on your phone's screen. If it does, grant it access.
- If the command fails, open **Magisk**, click on `Superuser`, find **Shell**, and grant it access.

## [Next step: Installing Windows](3-install.md)
