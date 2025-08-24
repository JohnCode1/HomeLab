# ⚙️ Installing Proxmox

## 💻 Hardware Requirements

For this guide, you will need:

* A USB drive.

* A computer to use as your home server.

* Another computer to connect to your home server.

* An Ethernet cable to connect your home server to your router.

## 💾 Software Requirements

* You need a program to convert your USB into a bootable drive to install Proxmox.

  * I recommend using **Rufus** for this.

## 📝 Guide

1. Go to the official Proxmox website and download the Proxmox VE ISO installer.

2. Go to the Rufus GitHub page, click on "Releases," and download the associated `.exe` file for your system (most likely `rufus-<version>.exe` for Windows 11).

3. Connect your USB drive to your computer. > ⚠️ **This process will wipe all data on the USB, so be sure to move anything you need to another location first.**

4. Open Rufus and select your USB drive as the device.

   * Select the downloaded Proxmox ISO image.

   * Click "Start" to install the OS to your USB drive.

5. Safely eject the USB drive from your computer using your OS's "Eject" function, then physically remove it.

6. **Back up all data from the machine you are turning into a home server, as this process will wipe the entire disk.**

   * If the machine used to run Windows, you might want to find the Windows product key to reuse it later on a VM or another machine.

7. Attach the Ethernet cable from your home server to your router.

8. Insert the USB drive into the home server and power it on.

9. Press the key to enter your BIOS or Boot Manager. (This key varies by manufacturer, but is often `F11`, `F12`, `F2`, or `Del`).

10. Select the USB drive to boot from.

11. Select **"Install Proxmox VE (graphical)"** and press enter.

    * Make sure the Ethernet cable is connected, as Proxmox will request an IP address from your router during this step.

12. Read and agree to the license agreement.

13. Select the disk where you want to install Proxmox. > ⚠️ **This will delete all data on this disk!** Click "Next."

14. Select your timezone, country, and keyboard layout.

15. Enter a secure password you won't forget and a valid email address, then click "Next."

16. Enter a hostname (a name for your server) and ensure the IP address is one that can be made static later.

17. The gateway and DNS server settings should not need to be changed unless you are using a custom configuration like AdGuard or Pi-hole. Click "Next."

18. Ensure "Automatically reboot after installation" is checked, verify the settings are correct, and click "Install." > ⚠️ **Warning: This will wipe the disk you selected.**

19. After the installation is complete and the machine has rebooted, navigate to `https://[your_server_ip]:8006` in your main computer's browser to access the Proxmox web interface.

    * If you get a warning, don't worry about it. This is because you have not set up security certificates, which we will do later.

20. Your login is `Username: root`. Enter the password you selected earlier and click "Login." I recommend saving your username.

21. A pop-up will appear indicating you are using the free version. Click "OK." Sometimes you have to press the **Escape** key if the pop-up doesn't go away.

22. I have found that my USB drive was not always unmounted correctly after the installation. I recommend clicking "Shutdown" in the top-right corner, removing the USB drive after it shuts down, and then restarting the machine and logging in again.

### Post-Installation Tweaks

#### Disable Enterprise Repositories

1. Navigate to your Proxmox node (the hostname you selected on the left under "Data Center").

2. Go to **"Repositories"**.

3. Click on the two enterprise repositories and then click **"Disable"**.

4. Click **"Add"** and enable the "No-Subscription" repository. This should be the first one on the drop-down list.

5. Finally, go to **"Updates"** and click **"Refresh."**

6. Upgrade your system by clicking **"Upgrade."**

   * Type `Y` in the terminal and press "Enter."

   * After it's finished, close the Proxmox Console Window.

### Additional Configurations

#### Optimize Storage Partition

* **Note:** Proxmox by default partitions your hard drive into two parts: one for the OS and one for your files. If you want to use the entire hard drive for your OS, follow these steps.

  * > ⚠️ **Warning:** This is a tricky process to undo. Only do this if you are sure.

  1. Open the shell and input the following commands:

  ```
  # Remove the logical volume for the file partition (replace with your volume name)
  lvremove /dev/pve/data 
  # Extend the root logical volume to use all free space
  lvresize -l +100%FREE /dev/pve/root 
  # Resize the file system to match the new logical volume size
  resize2fs /dev/mapper/pve-root
  ```

  2. Check the documentation if the commands don't work, as the volume name might be different.

#### Mount a Second Disk for Storage

* If you have another disk for storage, you can mount it here.

  * **Recommendation:** If you have the space and a second disk, it is highly recommended to use an SSD to run your apps and a large hard drive for storing your media. You can also run multiple hard drives in a **RAID pool** together, so if one fails, your data will be safe on the others.

  * If you only have two drives, keep your boot OS drive default and use the other for apps and media.

  * If you only have one disk, you have to use the default pool created for both apps and media. In this case, make sure you have backups exported to another device if you care about the data.

1. Navigate to `[hostname]` -> **"Disks"** -> **"ZFS"** -> **"Create: ZFS"**.

2. Select the drives you are creating a pool for. If you have multiple drives, select all the ones you will use.

3. Choose **"Single Disk"** for one disk or select the appropriate RAID configuration if using multiple drives.

   * I recommend searching for more information on RAID configurations, as there are many options, each with a specific use case.

4. Click **"Create"**.

#### PCIe Passthrough

* This will allow you to give a virtual machine direct access to a device, such as an Intel integrated GPU, an NVIDIA graphics card, or a USB port.

* The process is different for each device. Below are instructions for Intel integrated graphics and NVIDIA GPUs. Please refer to the Proxmox documentation for any other devices.

##### For Intel Integrated Graphics

1. In the shell of your Proxmox host, run `nano /etc/default/grub`.

2. Add the following line under the `GRUB_CMDLINE_LINUX=""` line to enable Intel IOMMU.

   ```
   GRUB_CMDLINE_LINUX_DEFAULT="quiet intel_iommu=on"
   ```

3. Press `Ctrl + O`, then `Enter`, and `Ctrl + X` to save and exit.

4. Run `update-grub`.

5. Run `dmesg | grep -e DMAR -e IOMMU` and `dmesg | grep 'remapping'` to verify that IOMMU and remapping are working correctly.

##### For NVIDIA GPU

* > ⚠️ **Note:** This process has not been retested, so you may need to do some additional research.

1. Verify that IOMMU and remapping are enabled using the commands above.

2. Edit the grub file again: `nano /etc/default/grub`.

3. Add the following line:

   ```
   GRUB_CMDLINE_LINUX_DEFAULT="iommu=pt"
   ```

4. Run `update-grub`.

5. Create a new file: `nano /etc/modules`.

6. Add the following lines to it:

   ```
   vfio
   vfio_iommu_type1
   vfio_pci
   vfio_virqfd
   ```

7. Create a new file: `nano /etc/modprobe.d/blacklist.conf`.

8. Add the following lines to it to blacklist the NVIDIA drivers:

   ```
   blacklist nouveau
   blacklist nvidia
   blacklist nvidiafb
   blacklist nvidia_drm
   ```

9. Run `lspci -v` to get a list of your PCI devices.

10. Find your GPU in the list and get its vendor and device ID. It will look like `[####:####]`.

11. Create a new file: `nano /etc/modprobe.d/vfio.conf`.

12. Add the following line, replacing the IDs with your GPU's IDs:

    ```
    options vfio-pci ids=10de:1b06,10de:10ef disable_vga=1
    ```

13. Run `update-initramfs -u`.

#### Create a Cluster

* > ⚠️ **Warning:** Undoing this is tricky. It is highly recommended to create a backup before doing this.

1. Navigate to **"Data Center"** -> **"Cluster"** and click **"Create Cluster."**

2. Give it a name and click "Create."

3. On the second machine, navigate to the same menu and click **"Join Cluster."**

4. Copy the join information from the first machine and paste it into the second.

Next: [Linux Container](../LinuxContainer) Layout: [Layout](../Layout)
