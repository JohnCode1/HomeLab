# 🐧 Creating a Linux Container

## What We Will Be Doing

* In this guide, we'll use a default Linux container to store media and run apps for your server. This is the **recommended approach** because containers are much more lightweight and efficient than full Virtual Machines (VMs).

## Creating a Container

* For this example, we're going to install **Ubuntu 24.04**, but you can use any Linux distribution you prefer.

1. Navigate to your Proxmox web interface and click on `<your-hostname>` -> **`local`** (`<your-hostname>`).

2. Click on **`CT Templates`**.

3. Click the **`Templates`** button.

4. Select `ubuntu-24.04-standard` and click **`Download`**.

5. Once the download is complete, click the "X" in the top right corner to exit.

6. Navigate to the top right of the Proxmox interface and click **`Create CT`**.

7. Enter a secure password for your container.

8. Select a **CT ID**. You can choose any number you'd like.

9. Input a **Hostname**. This will be the name of your container. For example, `media` or `storage`.

10. Click **`Next`**.

11. Select the container template you just downloaded.

12. Select the **ZFS Pool** to download your container to. This is the ZFS pool where your apps and OSes will be stored.

13. Select a **Disk Size**. I recommend starting with `32 GB` or larger.

14. Select the amount of **CPU Cores** to allocate. A good starting point is to allocate half of your total cores. You can always change this later in the container's resources settings.

15. Select the amount of **RAM** to allocate. Like the CPU cores, you can start with a generous amount and adjust it later as needed.

16. If you are not using a static IP address, select **`DHCP`** for your IP on either IPv4 or IPv6. If you're unsure, you're most likely using IPv4.

17. If you are using a static IP address, enter your **Gateway** and the IP address you want to use for the container. The gateway is most likely `192.168.1.1`.

18. Click **`Next`** again on the DNS page.

19. Verify that all the details are correct and click **`Finish`**.

20. Click on the container you just created in the left-hand navigation pane and then click on **`Resources`** in the main window.

    * This is where you can change the cores and RAM if needed.

21. If you want to add an extra disk for storing media, click **`Add`** -> **`Mount Point`**. Select your disk on the **`Storage`** dropdown.

22. Select the disk size.

23. Add a **Mount Path** (e.g., `/media` or `/docker`). This is where the storage will appear inside the container.

24. I recommend unchecking the **`Backup`** option for this mount point until you have configured your backup strategy. You can always perform manual backups if needed.

25. Click **`Create`**.

26. Repeat this process as necessary for any additional mounts you need.

    * For this guide, I recommend adding a separate `/data` mount and a `/docker` mount.

27. Click **`Start`** in the top-right corner to boot your container.

28. Open the container's shell and run these commands to update the system and add a new user. **Note:** You will need to replace `<name>` with the new username and `<mount-point>` with your mount path.

    ```
    # Update and upgrade all packages
    sudo apt update && sudo apt upgrade -y

    # Create a new user
    adduser <name>

    # Add the new user to the 'sudo' group for admin privileges
    adduser <name> sudo

    # Switch to the new user
    su <name>

    # Reboot the container
    sudo reboot

    # Remove the 'lost+found' directory from the mount point
    sudo rmdir /<mount-point>/lost+found

    # Change the ownership of the mounted directory to the new user
    sudo chown -R <user>:<user> /<mount-point>/

    # Repeat the last two commands for all additional mounts
    ```

Next: \[\[Linux VM]] Layout: \[\[Layout.md]]
