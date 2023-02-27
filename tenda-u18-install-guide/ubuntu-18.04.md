* TENDA U18-AX1800 with USB ID 0bda:8832

The TENDA U18-AX1800 comes with a configuration that appears to be a USB disk,
which contains a Windows driver. If a 'lsusb' command shows the ID 0bda:1a2b,
then this disk is mounted. The way to avoid this is to edit either file
/usr/lib/udev/rules.d/40-usb_modeswitch.rules, or
/lib/udev/rules.d/40-usb_modeswitch.rules, whichever is on your system, and add
the following lines:

# TENDA U18-AX1800 Wifi Dongle
ATTR{idVendor}=="0bda", ATTR{idProduct}=="1a2b", RUN+="usb_modeswitch '/%k'"


##### Installation with module signing for SecureBoot
For all distros:
```bash
git clone git://github.com/lwfinger/rtl8814au.git
cd rtl8814au
make
sudo make sign-install
```
You will be promted for a password, please keep it in mind and use it in next steps.

Reboot to activate the new installed module.
In the MOK managerment screen:
1. Select "Enroll key" and enroll the key created by above sign-install step
2. When promted, enter the password you entered when create sign key.
3. Select "Reboot".
4. Plug in your TENDA U18-AX1800 Wifi Dongle after log into your desktop account.
