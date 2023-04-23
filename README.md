## Arch Linux - VirtualBox Solution
Many users have reported issues when running VirtualBox on newer laptops. These issues are related to the incompatibility of VirtualBox with the newer CPUs. However, the good news is that these issues can be resolved with some tweaks. To install VirtualBox on Arch Linux, you can use the `pacman` package manager. Simply run the following command in a terminal window:

```
sudo pacman -S virtualbox
```

<br>

After installing VirtualBox, you may encounter an error message stating that "vboxdrv" kernel module is not loaded. This module is required to run VirtualBox on your system. To load the "vboxdrv" kernel module, you can run the following command in a terminal window:

```
sudo modprobe vboxdrv
```

<br>

If you encounter a freeze during virtual machine startup with an 11th generation Intel CPU, you can fix this by adding "ibt=off" as a kernel parameter. To add this parameter, open the `/etc/default/grub` file using a text editor like `nano` by running the following command in a terminal window:

```
sudo nano /etc/default/grub
```

<br>

Then, modify the `GRUB_CMDLINE_LINUX_DEFAULT` parameter to include "ibt=off". For example, the modified line may look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ibt=off"
```

<br>

Save the changes by pressing `Ctrl+O` and then exit the editor by pressing `Ctrl+X`. Finally, update the bootloader configuration using the following command in a terminal window:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

<br>

Finally, reboot your system for the changes to take effect.

```
sudo reboot now
```
