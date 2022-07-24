Just run "io.clave2/io.clave2.lcshell_unpacker/unpacker.py" with Python3.

You'll probably run with an error saying that the device can´t be opened, to fix that you need to make an udev rule.
You need to figure out the USB bus on which the dongle is located on and add an udev rule to "/etc/udev/rules.d/" with the name "99-usb-dongle.rules".

You'll need to use a text editor with elevated privileges, I use "sudo nano" in "/etc/udev/rules.d/" to create the file.

You paste the contents with right click -> Paste and CTRL+O to save, it'll ask for the file name ("99-usb-dongle.rules"), you press enter and reboot your system.

The udev rule contents are:

SUBSYSTEM=="usb", ATTRS{idVendor}=="1bc0", ATTRS{idProduct}=="8101", MODE="0666"

KERNEL=="hidraw*", ATTRS{busnum}=="<YOUR_BUS_NUMBER_HERE>", ATTRS{idVendor}=="1bc0", ATTRS{idProduct}=="8101", MODE="0666"

Dependencies:

![image](https://user-images.githubusercontent.com/2711997/178621672-7cba6a63-bcc1-46e8-bd03-7a3b59386135.png)
