# 💻 Installing and Setting Up a Linux VM

## What We Will Be Doing

* We will be creating a **Virtual Machine (VM)** and installing applications onto it.

  * A more secure approach is to install each application on a separate VM. This guide combines them to save on resources, but be aware of the security trade-off. If one app gets compromised, all apps on that VM may be at risk.

  * While containers are more lightweight, VMs offer more flexibility and features.

  * For this guide, we'll use **Ubuntu Server 24.04**, but you can choose any Linux distribution you prefer.

## Installing a Linux VM

1. Go to the [Ubuntu Server download page](https://ubuntu.com/download/server "null"), right-click the "Download now" button, and copy the download link.

2. In your Proxmox web interface, navigate to `<your-hostname>` -> **`local`** (`<your-hostname>`) -> **`ISO Images`**.

3. Click **`Download from URL`**, paste the link, and click **`Query URL`** -> **`Download`**.

4. Once the download is complete, click **`Create VM`** in the top-right corner.

5. On the "General" tab, enter a **VM ID** and a **Name**.

6. Click **`Next`**. On the "OS" tab, select the Ubuntu ISO image you just downloaded.

7. Select the storage pool to run the VM on. This is where the virtual disk will be stored.

8. On the "System" tab, leave the default settings and click **`Next`**.

9. On the "Disks" tab, select your storage and the disk size you want for the VM.

10. On the "CPU" tab, choose the number of CPU cores you want to allocate. Change the **Type** at the bottom to **`host`** for better performance.

11. On the "Memory" tab, choose the amount of RAM to allocate to the VM.

12. On the "Network" tab, leave the default settings unless you have a specific network configuration.

13. On the "Confirm" tab, review your settings, and then click **`Finish`**.

## Enabling Hardware Transcoding

* This process is for Intel Hardware Transcoding. It allows the VM to use your CPU Graphics for tasks like video encoding, which can significantly improve performance for apps like Jellyfin. > ⚠️ **Warning:** If using a laptop or some device with a screen you will most likely loose video to that screen

 * Navigate to your Proxmox host -> Hardware -> Add PCIE device -> Raw Device-> select device (If using a cpu it most likely wil be <cpu name> Graphics -> check all functions -> ADD.


14. Once the VM is created, select it in the left-hand pane and click **`Start`** in the top-right corner.

15. In the console, select **`Install`** and press enter.

16. Select your language and keyboard layout.

17. Select **`search for third-party drivers`** and `ubuntu server`.

18. Leave the network and proxy settings alone.

19. Wait for it to check for the mirror location.

20. Deselect **`set up this disk as an lvm group`** and then hit continue.

21. Select your file system and click **`continue`**.

22. > ⚠️ **Warning:** This step will wipe the selected VM's data. Hit **`continue`** again.

23. Input your server name, username, and password.

24. Skip the Pro-only options for now.

25. Select **`openssh`** if desired, as it's helpful for remote access.

26. Do not select any other apps for now.

27. When the installation is finished, navigate to the **`Hardware`** tab of your VM -> **`CD/DVD Drive`** -> **`local:iso/ubuntu24.04`** -> **`Remove`**.

28. Go back to the **`Console`** and select **`Reboot Now`**.

29. After the reboot, press enter and log in with the user you created.

30. Run `sudo apt update && sudo apt upgrade -y` to update the VM.

31. Run `sudo reboot` 


Next: [Samba](../Samba) Layout: [Layout](../Layout)
