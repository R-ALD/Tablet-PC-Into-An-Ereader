## Make your computer tablet into an Ereader

### 0. If your device's UEFI firmware is 32-bit (As my DELL venue 8 pro does)
After creating a bootable USB (Prefferably using **rufus**):
- Download the 'bootia32.efi' from this repository.
- Put the 'bootia32.efi' file into the boot drive's folder:
```bash
/EFI/BOOT/
```
Then your boot drive should be ready to go.

### 1. Download Debian 13 terminal only

Create a user called 'remoteuser' (Even if you won't be using SSH)
The password should be easy to remember.

At software selection check only these two:
[x] SSH server (Optional but recommended)
[x] standard system utilities

(Using SSH you can just paste in the following commands from your computer instead of typing them in manually on the tablet's small screen)

### 2. Make tablet run Koreader at startup
Once the device boots up:
- Log in as 'root'.
- Run this command.
```bash
wget -O downloader.sh "https://raw.githubusercontent.com/R-ALD/Computer-Tablet-Into-Ereader/refs/heads/main/downloader.sh" && bash downloader.sh
```
- Once the device has rebooted, on its own, it should boot into koreader straight away.

If you want to go back to terminal press 'Ctrl + Alt + F2'

#### 2.0 Change screen settings
I recommend doing this while being in 'Koreader' on your tablet and using ssh from your computer, to see the changes live.

#### 2.1 Screen brightness
To change brightness use this command:
```bash
echo INSERT_BRIGHTNESS_HERE > /sys/class/backlight/intel_backlight/brightness
```

Replace 'INSERT_BRIGHTNESS_HERE' with a value in the range 1-100.

#### 2.2 Night mode
To run night mode, run the command:
```bash
nightmode
```
Clear instructions on how to proceed will be displayed.

### 3 (Optional) Create a Wi-Fi switch so it won't run in the background

To create the switch run this command as root:

```bash
wget -O wifiSwitchInstaller.sh "https://raw.githubusercontent.com/R-ALD/Computer-Tablet-Into-Ereader/refs/heads/main/wifiSwitchInstaller.sh" && bash wifiSwitchInstaller.sh
```

To use it run:
```bash
wifiswitch
```
Clear instructions on how to proceed will be displayed.
