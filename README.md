# Welcome!
  [![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0.en.html) [![ko-fi](https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/johnep) [![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/your-discord-server-invite-link)

---
## 🌟 Current Status of project
I currently made a change to the structure of the guide and links currently do not work. Will fix soon, but wanted to commit these to see what it looks like on github.
The current state of this guide is a compilation of my notes when using the below resources to make my home server I have gone through and double checked the current status of this guide on a new proxmox server and verified everything will run. If you have any questions or get stuck somewhere please reach out to me on discord or check out the app's documentation.

* If you get an issue spinning up a docker container check the release version is correct.
### NEW ADDITIONS: Changed layout to a single page, and moved dockerfiles to there own repository.
* I have made alot of changes to the structure of this and altered my docker compose files to be more up to date with the latest versions in my homelab.
    * This guide has not been retested from start to finish since changes so there might be a small issue. 
---

## 🌟 About This Project

This guide is designed to make setting up a homelab more accessible to those who are less involved in the technology world and to make the initial setup process easier and faster. I use this guide for my own personal homelab as a quick reference if i forgot a command.

> ⚠️ **Caution:** This guide is intended for educational purposes. Any hardware damage or security breaches that may occur when using this guide are at your own risk.

---

## 🎯 Who This Is For (And Who It Isn't)

* ❌ Homelabs are **not** for someone who wants to set it up once and never touch it again. While you could argue that if you never open it to the worldwide web, you would be safe even if a security flaw is found later, you would be doing so at your own risk.
* ✅ This is for someone who wants to reduce or completely eliminate their subscription fees.
* ✅ This is for someone who loves to tinker with things.

---

## 🤝 References

A huge thank you to all the people referenced below—this project would not be possible without them. The people below have not given any direct advice to me or direct contributions, but I have learned alot from their videos or documentation.

* **[TechhutTV](https://techhut.tv/)** - This creator helped me get started with my homelab and is the original main basis for my setup.
* **[LawrenceSystems](https://lawrencesystems.com/)** - Lawrence's videos are the initial basis for my networking software, hardware, and knowledge.
* **[HardwareHaven](https://www.hardwarehaven.media/)** - A helpful channel about hardware.
* **[Jeff Geerling](https://www.jeffgeerling.com/)** - A helpful channel on hardware and homelabs with a focus on Raspberry Pi.
* **[Raid Owl](https://raidowl.com/)** - A helpful channel on hardware and software.
* **[Techno Tim](https://technotim.live/)** - A helpful channel on hardware and software.
* **[LinusTechTips](https://linusmediagroup.com/)** - A helpful channel for hardware and software.

---


# 📚 Structure of this Guide and How to Use It
* All of my current docker compose files and scripts are in separate repositories for apps.

* 🔄 It is perfectly fine to follow this guide **out of order** and choose what you want to implement. However, be aware that you may need to make some tweaks depending on where you start.

  * > **Example:** If you do not use the file setup that I have, you will have to adjust your own setup accordingly.

* 🧭 At the end of each page, after the link to the next section, I will include a link to get back to the table of contents for easy navigation.
    
# 📖 List of All Pages

* [About Project](../..)

* [HardwareSelections](../Hardware)

* [UsefulInfo](../UsefulInfo)

* [Proxmox](../Proxmox)

* [Linux Container](../LinuxContainer)

* [Linux VM](../LinuxVM)

* [Samba](../Samba)

* [Backup](../Backup)

* [Docker](../Docker)

* [Nginx Proxy Manager](../Ngix)

* [Windows VM](../WindowsVM)

* [Glance](../Glance)

* [Immich](../Immich)

* [Fresh RSS](../FreshRSS)

* [Karakeep](../Karakeep)

* [It Tools](../ItTools)

* [Torrent/Usenet](../TorrentUseNet)

* [Jellyfin](../Jellyfin)

* [Metube](../Metube)

* [CyberChef](../Cyberchef)

* [Desktop Programs](../DesktopPrograms)

* [Other Apps](../OtherApps)

* [Roadmap](../RoadMap)

* [NextCloud](../NextCloud)

* [Server Data Monitoring](../ServerMonitoring)


---
**Layout:** [Layout](./Guide/Layout)
# 💻 Hardware Recommendations

* The type of hardware you use is totally up to you.

* If you plan on using apps that might require **hardware acceleration** (e.g., Jellyfin), if you don't plan on using a gpu consider using an **Intel CPU** due to their internal graphics.

* To get started and reduce initial costs, use an old computer that you are no longer using.

  * 💡 I personally use an old laptop with a busted screen for this purpose.

* There are a plethora of mini PCs out there that you can find new or used for a fairly cheap price.

* If you are considering storing a lot of media and have the budget, look into getting a **NAS (Network Attached Storage)**.

  * There are some mini NAS options that are cheaper than a normal NAS.

* Before buying any new equipment, especially on a tight budget, keep in mind that you might want to get a setup where you can change out components in the future, as you might not be able to run everything you want at that moment.

  * > **Example:** Building your own mini PC.

* If you plan on running **local LLMs**, look into a setup that supports attaching a **GPU**.

  * This is not required, as I was able to run some small LLMs on my old laptop fairly decently, but note that you will not get the same quality and speed as a setup with a GPU.

# ⚙️ My Current Setup

* **Lenovo Ideapad 1:** This is my main workstation I use to connect to my VMs.

* **Old busted screen HP laptop:** This is currently running Proxmox.

* **Custom-built PC:** This used to be my main workstation and is now also running Proxmox.

  * I swapped most of my apps from my laptop to this machine. When I need a Linux or Windows desktop, I just spin up that VM.

  * While this does result in some performance loss compared to running the OS directly, it does not affect me with my current hardware and use case.

# ✅ Bare Minimum Requirements

* A computer to connect to your Proxmox server.

* A computer to run Proxmox that you can plug an Ethernet cable into.

  * The recommended way to use Proxmox is via Ethernet.

* A USB drive to install Proxmox on.

* An Ethernet cable.

* A router with an open Ethernet port.

> ⚠️ **Warning:** If you are using a laptop, it is recommended to remove the battery, as it could potentially swell from being constantly plugged in.

Layout: [Layout](../Layout)
# 🧠 Useful Information

## 🌐 Networking

* ⚠️ **Caution:** Networking can be complicated and I am still learning alot about network security. The main thing I recommend is to not open any ports/foward anyports to the WAN.
* When you go through this guide, you will need to know a little about your current network. First, let's talk about the distinction between **WAN IPs** (Public IPs) and **LAN IPs** (Local/Private IPs).

* When connecting to the internet, your ISP (Internet Service Provider) assigns your router a public IP address. This address is how the outside world communicates with your home network. Your public IP can change over time depending on your ISP.

* Every time you connect a device (like your computer, phone, or home server) to your internet via Wi-Fi or an Ethernet cable, your router assigns it a private IP address.

  * This happens because your router creates a **Local Area Network (LAN)** that is isolated from the internet. Most default setups use a network in the IP ranges of `192.168.1.1` to `192.168.1.255`. This is often written as `192.168.1.0/24`.

  * In this case, your router acts as the **"gateway"** on IP `192.168.1.1` and assigns each device an IP address via **DHCP** (Dynamic Host Configuration Protocol).

* If you plan on changing your LAN IP, which is often a good security practice, do a quick search online to find what IP ranges are allowed for LAN networks.

* You might want to consider upgrading your router or getting a dedicated **firewall**.

  * I currently use **pfSense** as a firewall, which can be a little tricky but gives you a lot of advanced options.

  * Another popular brand is **Unifi**. They generally offer "gateways" that are a combination of a router and a firewall.

* **I do not recommend opening any ports on your router to the WAN (port forwarding)**. Port forwarding is the process of allowing outside connections to a specific device on your internal network. This can be a security risk as it exposes your home server to the entire internet.

* A much safer way to connect to your home server from outside your home is by using an **overlay VPN**. This creates a secure, private tunnel to your home network, allowing only authorized users to access it. This method greatly reduces your attack surface compared to port forwarding.

* Later in this guide, we will get a domain name via **Cloudflare**, which is not required but makes it easier to access your services by using a human-readable name (e.g., `myserver.com`) instead of an IP address. There are free options out there but be careful of scams. Lastly you can use a local domain name of whatever you want without having to purchase anything. You will just have to configure your router/overlayvpn to route to that domain name to the ip of your reverse proxy.

  * ⚠️ **Warning:** When purchasing a domain, make sure the TLD (e.g., `.com`, `.net`, `.org`) allows for **WHOIS masking**. This feature hides your personal registration information from the public. The `.us` TLD, for example, does **not** allow this. Always search for "WHOIS privacy" for a domain provider before you buy.

  * You should be able to find a good domain name for about `$7 - $12` per year. Be cautious of providers with expensive renewal fees. Again there are free options or you can get away without having a public domain as in this guide we keep it all local.

## 🖥️ Proxmox

* **Proxmox** is a powerful, open-source server virtualization management platform. It allows you to create and manage both Virtual Machines (VMs) and containers from a single web interface.

* Once everything is set up, it works very well. However, if you run into problems, it can get complicated fast. Sometimes, it's easier to restart from scratch than to try and fix a small mistake.

* **Proxmox Quirks:** Without a paid subscription, a pop-up will appear when you log in. You can simply press the **Escape** key to close it if the "OK" button doesn't work.

* **Clustering:** This means running multiple PCs together as a single unit to share resources and provide redundancy. This is an advanced topic, and once you cluster machines, it is very difficult to separate them.

## 🐧 Linux

* **Linux** is an open-source operating system that is widely used for servers and home labs. This guide uses it for many of the applications and server management tasks.

* Here are some essential basic commands you will need:

  * `ls`: **L**i**s**ts the files and directories in your current location.

  * `cd [directory]`: **C**hanges **d**irectory. For example, `cd documents` moves you into the "documents" folder.

  * `cd ..`: Moves you **up** one level from your current directory.

  * `cd ~`: Takes you to your user's home directory.

  * `mkdir [name]`: **M**a**k**es a new **dir**ectory (folder).

  * `rm [file]`: **R**e**m**oves (deletes) a file. Be careful—this is permanent!

  * `pwd`: **P**rints the **w**orking **d**irectory (shows you where you are).

  * `sudo`: Stands for **S**uper**u**ser **do**. It allows you to run a command with administrative or root privileges. Use this command with caution.

  * You can run multiple commands at once using `&&`. For example: `command1 && command2` will run `command2` only if `command1` is successful.

## 🗄️ VMs and Containers: What's the Difference?

* **Virtual Machines (VMs)**: Think of a VM as a complete, separate computer running inside your main computer. It has its own operating system (OS), virtual hardware (CPU, RAM, storage), and applications. This offers full isolation but uses more resources.

* **Containers**: Think of a container as a lightweight, isolated application running on your existing OS. It shares the host's OS kernel but has its own file system and libraries. This is much more efficient and uses fewer resources than a VM.

## 🐳 Docker Containers

* **Docker** is a platform that makes it easy to create, deploy, and run applications in containers.

* The way it works, in simple terms, is that developers create **"images"**—these are read-only templates that contain the application and all its dependencies. For example, an image might say, "use the Linux 24.04 OS and download Python."

* You can run a container by specifying an image from **Docker Hub**, which is a public repository of images.

  * ⚠️ **Warning:** Only use trusted and official sources from Docker Hub.

* **Key Commands:**

  * `docker run [image] -d`: Runs the image in a new container. The `-d` flag runs it in the background (**d**etached) so it doesn't take over your terminal.

  * `docker ps -a`: Lists all running and stopped containers (`-a` for **a**ll).

  * `docker stop [container name]`: Stops a running container.

  * `docker --help`: Displays a list of all Docker commands.

* For more complex applications, we will use **Docker Compose**, which is a tool for defining and running multi-container Docker applications.

  * This uses a `compose.yml` file to specify all the images you need, along with their settings and configuration options.

  * `docker compose up -d`: Starts all services defined in the `compose.yml` file.

  * `docker compose down`: Stops and removes the services defined in the `compose.yml` file.

## 🔒 Helpful Privacy Tips

* A key benefit of self-hosting is that you have more control over your data. With services like Google Cloud, you cannot prevent them from accessing your data as they see fit.

* A few ways to enhance your privacy with little effort:

  * **Use a VPN (Virtual Private Network).** This encrypts your internet traffic, hiding your activity from your ISP. Just be sure to choose a reputable VPN provider that has a no-log policy.

  * **Use a privacy-focused browser.** For example, Firefox allows you to set strict privacy modes.

  * **Install privacy-focused extensions.** Examples include **uBlock Origin** (to block ads and trackers) and **Privacy Badger** (to automatically block trackers).

  * **Consider using a service like Kasm.** This is not necessary for most users, but it can be useful if you're ever afraid to click on certain links. It creates a temporary, sandboxed environment that is easily destroyed, so any malicious code cannot affect your main system.

* **Use a Password Manager:** This is a crucial step for securing your homelab and all your online accounts. A password manager helps you create and store unique, strong passwords for every service, so a single breach doesn't compromise all your accounts.

## 🔒 My setup

* Below I have specific things I have done specifically to my set up

  * **VPN**
   * The provider I use is Private Internet Access(PIA) set up with obstufication to allow me to still access websites that block using a vpn this is set up at the router level and routes all my traffic through the vpn
  * **Net Bird**
   * I have net bird to access local resources when not home. This allows a more secure way to access then opening ports on my pfsense
   * I use endpoint routing to route all my traffic through a ip that is routed through my PIA VPN so all of my traffic is then routed through the VPN.    
  * **PFSense**
   * I have alot of customization in this but will highlight some of the changes ive made
    * Using PFNG Blocker to block list. I do this for extra protection against accidentally going to Ips that may be trying to steal my information
    * I set up a custom rule to route all my domain name request to my nginx.(A set up up like this allows you to avoid buying a public domain name)
    * I have two lans set up to isolate my server from all my other devices.
 
  * **Running seperate Containers/VMS**
   * I have set up multiple containers/VMS to isolate my machines
  * **Linux OS**
    * I have finally got tired of microsoft and swapped to primary OS of Arch Linux.
    * There is a newer prebuilt setup of Arch called omarchy which is just a bunch of shell scripts to customize Arch.
    * This set up was perfect for me as I like the graphics of the set up and I am able to tweak anything I want in it to learn.
    * There is a article I read about some potential not best practices being used in omarchy, but my take is that I am not too worried and going to take that information to further my setup of arch.
    * For someone looking for a simpler setup I recommend checking out Ubuntu, or Pop OS.

Next: [Layout](../Layout)
# ⚙️ Installing Proxmox

## 💻 Hardware Requirements

For this guide, you will need:

* A USB drive.

* A computer to use as your home server.

* Another computer to connect to your home server.

* An Ethernet cable to connect your home server to your router.

## 💾 Software Requirements

* You need a program to convert your USB into a bootable drive to install Proxmox.

  * I recommend using **Rufus** for this. or another alternative is balena etcher.

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

##### For Intel/amd IOMU

1. In the shell of your Proxmox host, run `nano /etc/default/grub`.

2. Add the following line under the `GRUB_CMDLINE_LINUX=""` line to enable Intel IOMMU.

   ```
   #Change intel -> amd for amd
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

#### Check actual amount of data vs. data allocated:
* Run to see how much memory you have allocated vs how much is available via zfs:
  ```bash
  zpool list 
  zfs list
  ```
Layout: [Layout](../Layout)
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
## Enabling Hardware Transcoding

* This process is for Intel Hardware Transcoding. It allows the VM to use your CPU Graphics for tasks like video encoding, which can significantly improve performance for apps like Jellyfin. > ⚠️ **Warning:** If using a laptop or some device with a screen you will most likely loose video to that screen

   1. Navigate to your Proxmox host -> **`Shell`**.

   2. Run `nano /etc/pve/lxc/<container id>.conf`.

   3. Add the following lines to enable hardware transcoding:

      ```bash
      # Intel Quicksync
      dev0: /dev/dri/card0,gid=44
      dev1: /dev/dri/renderD128,gid=104
      ```
27. Click **`Start`** in the top-right corner to boot your container.

28. Open the container's shell and run these commands to update the system and add a new user. **Note:** You will need to replace `<name>` with the new username and `<mount-point>` with your mount path.

    ```bash
    # Update and upgrade all packages
    apt update && apt upgrade -y
    ```
    ```bash
    # Create a new user
    adduser <name>
    ```
    ```bash
    # Add the new user to the 'sudo' group for admin privileges
    adduser <name> sudo
    ```
    ```bash
    # Switch to the new user
    su <name>
    ```
    ```bash
    # Reboot the container
    sudo reboot
    ```
    ```bash
    # Remove the 'lost+found' directory from the mount point WARNING MAKE SURE THERE WAS NO IMPORTANT DATA ON THAT DRIVE
    sudo rmdir /<mount-point>/lost+found
    ```
    ```bash
    # Get user Id number
    id
    ```
    ```bash
    # Change the ownership of the mounted directory to the new user
    sudo chown -R <useidr>:<userid> /<mount-point>/
    ```
    # Repeat the last two commands for all additional mounts
    ```

Layout: [Layout](../Layout)
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

30. Run to update the VM.```bash
        sudo apt update && sudo apt upgrade -y
        ```
    
32. Run `sudo reboot`

33. make any directories you want and change permision to you `sudo chown -R <username>:<username> /<path>` 


## If using hardware transcoding

32. run the following to verify devices are there that you are using. You should see something like card0, card1, rednderD128
    ```bash
    ll /dev/dri
    ```
    
33. to enable user to use hardware transcoding run
    ```bash
    sudo usermod -aG render <user name>
    ```
    
34. If using intel install intel-gpu-tool
    ```bash
    sudo apt install intel-gpu-tools
    ```
    
35. verify running properly
    ```bash
    intel_gpu_top
    ```
36. `cntrl^C` to exit

Layout: [Layout](../Layout)
# 📂 Purpose of Samba and What We Will Be Doing

* The purpose of Samba is to enable remote connections to your shared files.

* Later in the guide, we'll create a VM to run apps, and we can use Samba to connect that app VM to these files, keeping all your data in one central location.

* **Note:** Some apps require additional workarounds for this setup. For example, some users have reported issues running Jellyfin and torrent applications via Docker with this configuration, and had to create a separate folder on that VM to store the Docker files.

# 🔧 Installing and Setting Up Samba

1. Navigate to the VM or container you designated for media storage.

2. Run the following command to install Samba and then enter your password:

   ```
   sudo apt install samba -y
   ```

3. Edit the Samba configuration file:

   ```
   sudo nano /etc/samba/smb.conf
   ```

4. Insert the following variables and adjust them for each path you need. This example uses paths for media, and docker but repeat for each path you have.

   ```
   [global]
      server string = <hostname>
      workgroup = WORKGROUP
      security = user
      map to guest = Bad User
      name resolve order = bcast host
      hosts allow = <base ip>/<subnetmask> ex. 192.168.1.0/24
      hosts deny = 0.0.0.0/0
   [<name of path>]
      path = /<path>
      force user = <user name>
      force group = <user name>
      create mask = 0774
      force create mode = 0774
      directory mask = 0775
      force directory mode = 0775
      browseable = yes
      writable = yes
      read only = no
      guest ok = no
   [<name of path 2>]
      path = /<path 2>
      force user = <user name>
      force group = <user name>
      create mask = 0774
      force create mode = 0774
      directory mask = 0775
      force directory mode = 0775
      browseable = yes
      writable = yes
      read only = no
      guest ok = no
   ```

5. Press `Ctrl + O` to save, then `Enter` and `Ctrl + X` to exit.

6. Create a Samba password for your user:

   ```
   sudo smbpasswd -a <username>
   ```

7. Set the Samba services to automatically start on reboot:

   ```
   sudo systemctl enable smbd
   sudo systemctl enable nmbd
   sudo systemctl restart smbd
   sudo systemctl restart nmbd
   ```

8. If your main computer is running Windows, install the Windows discovery service:

   ```
   sudo apt install wsdd
   sudo apt install wsdd-server
   ```

9. If you have a firewall and are experiencing issues, allow the necessary services:

   ```
   sudo ufw allow OpenSSH
   sudo ufw allow Samba
   sudo ufw allow 3702/udp
   sudo ufw allow 5357/tcp
   sudo ufw allow 5358/tcp
   sudo ufw status
   sudo ufw enable
   ```

   * You should now be able to access these directories on your local network (LAN).

# 🔗 Connecting to the Samba Share on a Linux VM

10. On the server you want to connect to your media server, install `cifs-utils`:

    ```
    sudo apt install cifs-utils -y
    ```

11. Edit the `/etc/fstab` file to automatically mount the Samba share on startup:

    ```
    sudo nano /etc/fstab
    ```

12. Add the following lines to the file, replacing the placeholders with your information. For this I created two shares one for media and one for docker

    ```
    //<ip of media server>/<path1> /<path1 cifs uid=1000,gid=1000,credentials=/home/<username>/.smbcredentials,iocharset=utf8 0 0
    //<ip of media server>/<path2> /<path2> cifs uid=1000,gid=1000,credentials=/home/<username>/.smbcredentials,iocharset=utf8 0 0
    #Working on creating a seperate share for next cloud when added to this guide
    //<ip of media server>/<path3 this one is specific for next cloud> /<path3> cifs rw,mfsymlinks,seal,credentials=/home/<username>/.smbcredentials,uid=33,gid=0,file_mode=0770,dir_mode=0770 0 0
    ```

13. Create a `.smbcredentials` file to store your Samba login information:

    ```
    sudo nano /home/<user>/.smbcredentials
    ```

14. Add these lines to the credentials file:

    ```
    user=<username on media server>
    password=<password on media server>
    ```

15. Press `Ctrl + O` to save, then `Enter` and `Ctrl + X` to exit.

16. Reload the system daemon, create paths, and mount the drives:

    ```
    sudo mkdir <path1>
    sudo mkdir <path2>
    sudo systemctl daemon-reload
    sudo mount -a
    ```

17. Change the ownership of the mounted directories, first get your user id than change ownership with your id:

    ```
    id -u
    sudo chown -R 1000:1000 /<path1>
    sudo chown -R 1000:1000 /<path2>
    ```
# Connecting VIA Containers:
1. navigate to shell of main node and run if not remapping your ids add 100000 please see -> for remapping ids https://pve.proxmox.com/wiki/Unprivileged_LXC_containers
```bash
mkdir /mnt/data
mount -t cifs -o username=<>,password=<>,uid=<id>,gid=<gid> //192.168.1.1/data /mnt/data
```
2. navigate to `/etc/pve/lxc/YOUR_CONTAINER_ID.conf` and add
   ```bash
   mp0: /mdata,mp=/datamount
   ```
# 📁 Creating File Paths

* Use the following commands to create the file paths that will be used for future applications in this guide:

```
mkdir -p downloads/qbittorrent/{completed,incomplete,torrents} && mkdir -p downloads/nzbget/{completed,intermediate,nzb,queue,tmp} && mkdir -p books/ && mkdir -p movies && mkdir -p music && mkdir -p shows && mkdir -p youtube
```

Next: [Backup](../Backup) Layout: [Layout](../Layout)
# 🔄 Setting up Backups
### **Method 1: Manual Backups (Quick & Simple)**

This method is useful for a quick backup or if you have limited resources.

1. Navigate to the VM or container you want to back up.

2. Click the **`Backup`** tab.

3. Click **`Backup now`**.

4. For the `Mode` setting, select **`Snapshot`**. This will create a snapshot of your VM.

5. Click **`Backup`** to start the process.

### **Method 2: Using a Dedicated Proxmox Backup Server (Recommended)**

This is the recommended approach for a more professional and reliable setup. A dedicated backup server allows for scheduled backups, efficient data deduplication, and a centralized location for all your backup files.

#### **Software Requirements**

You will need the Proxmox Backup Server ISO image. You can download this from the official Proxmox website.

#### **Guide**

1. **Install the Proxmox Backup Server:** Install the Proxmox Backup Server ISO onto a separate VM or physical machine. Recomened giving it 32 GB of memory

   * Give it a name, such as `backup.local`.

   * Select your disk for the OS and storage.

   * Assign the desired number of CPU cores and RAM.

2. **Initial Setup:** Log in to your new Proxmox Backup Server using the web interface and run the promox Community Post install script. Select yes to all except for pbe test


3. **Get the Fingerprint and Configure BackUp Server:**

   * Go to the **`Dashboard`** of your Proxmox Backup Server. EX. 192.168.1.1:8007
  
   * Create a ZFS Pool for your storage set comporession to `lz4`

   * Find and copy the **`Fingerprint`**. This unique ID is a security key used to connect your main Proxmox host to this backup server.

4. **Connect to Your Main Proxmox Host:**

   * Navigate to your **main Proxmox host**'s web interface. 

   * Click on **`Datacenter`** -> **`Storage`**.

   * Click **`Add`** -> **`Proxmox Backup Server`**.

   * Enter the credentials for your backup server.
  
     * Root@pam for username
    
     * Select an id name of your choice
    
     * Enter IP of proxmox back up server
    
     * Datastore is name of server

     * Paste the **`Fingerprint`** you copied earlier 

6. **Configure Backup Job:**

   * Navigate to **`Datacenter`** -> **`Backups`**.

   * Click **`Add`** to create a new backup job.

   * Select the **node** you want to back up.

   * Choose the **Proxmox Backup Server** as the backup destination.

   * Select a **schedule** (e.g., daily, weekly).
  
   * Select VMS to Backup

   * Set the **`Retention`** policy (how many backups to keep).

   * Set the **`Mode`** to **`Snapshot`**.
  
   * Verify Backups enable on disk for vms/containers
  
     * for containers go to resources select disk and ensure backup is checked
    
     * for vms go to hardware click on your disk select advanced and verify backup is checked.

7. **Test the Backup:**

   * To verify everything is working, select your VM or container.

   * Go to the **`Backup`** tab and click **`Backup now`**.

   * Your new backup job should appear in the dropdown. Select it and click `Backup` to run an immediate test.
  
  Layout: [Layout](../Layout)

# 🐳 Installing Docker

## 💻 Installation Steps

Follow these steps to install Docker on your system. These commands will download and install Docker and then set up your user account to use it without needing `sudo` every time.

1. **Download the Docker installation script.** This command uses `curl` to download the official Docker installation script and saves it as `get-docker.sh` in your current directory.

   ```
   #if on a container first run this to get curl
   sudo apt install curl
   curl -fsSL https://get.docker.com -o get-docker.sh
   ```

2. **Run the installation script.** The `sudo sh` command runs the script with administrative privileges, which is required to install Docker and all its dependencies.

   ```
   sudo sh get-docker.sh
   ```

3. **Verify that Docker is running.** After the installation, you can use `systemctl` to check the status of the Docker service. Look for the word `active` in the output to confirm it's running correctly. `cntrl^c` to exit

   ```
   sudo systemctl status docker
   ```

4. **Create the Docker group.** This step creates a special user group called `docker`. This group is a key part of the setup, as it will allow your user to run Docker commands without needing `sudo` every time.

   ```
   #this group should already be made but i do it just to check
   sudo groupadd docker
   ```

5. **Add your user to the Docker group.** This command adds your current user (`$USER`) to the newly created `docker` group. This is what enables you to run Docker commands without root privileges.

   ```
   sudo usermod -aG docker $USER
   ```

6. **Activate the new group changes.** The changes to your user's group membership won't take effect immediately. You can either log out and log back in, or you can run this command to refresh the group permissions in your current shell.

   ```
   newgrp docker
   ```

7. **Remove the installation script.** Once Docker is installed, you no longer need the installation script. This is a good practice to keep your system clean.

   ```
   rm get-docker.sh
   ```

   To be extra sure of the file name before removing it, you can run `ls` to list the files in your current directory.
**NOTE:
For apps jellyfin, nextcloud, and QbitUsenet the docker files must be stored locally on that machine and can not use samba. After creating a directory run the following to make sure docker can read and write and those directories
   ```bash
    sudo chown -R <id>:<id> /<path1>
    sudo chown -R <id>:<id> /<path2>
    sudo chown -R <id>:<id> /<path3>
   ```

    Layout: [Layout](../Layout)
    # 🌐 Setting up Nginx Proxy Manager
* Warning you are now entering a area where small things matter. Depending on your network set up you may have to change things around.

## What We Will Be Doing

* In this section, we will use **Nginx Proxy Manager** 

* The Nginx Proxy Manager container will act as a reverse proxy, handling all incoming web traffic and routing it to the correct app (like Jellyfin).


## **Guide**

1. **Obtain a domain name.** Go to a domain provider of your choice (like Cloudflare) and purchase a domain name. **⚠️ WARNING:** Make sure the TLD (e.g., `.us` or `.net`) allows for masking your information to prevent spam.

2. **Configure DNS records.** In your DNS provider's settings, add the following records:

   * **Type A record:** with the name `@` and your public IP address.

   * **Type CNAME record:** with the name `*` and your domain name.

   * **Important:** Disable the proxy feature on the DNS provider. This is crucial for self-hosted apps, especially streaming services like Jellyfin, to avoid violating terms of service.
  
   * * **Important:** if you have a firewall or router that suports host or dns over ride use that instead. 

3. **Get a Cloudflare API Token.**

   * Go to your profile and create a new API token.

   * Use the "Edit zone DNS" template.

   * Include all zones, then continue to the summary and copy the API token.

4. **Run the containers.**

   * Navigate to the directory where your storing your docker files and mkdir for ngix.
     ```bash
     mkdir ngix
     cd ngix
     wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/nginx/compose.yml
     ``` 

   * Run the following command to start the containers in the background:

   ```bash
   docker compose up -d
   ```

5. **Verify the containers are running.**

   ```bash
   docker compose logs
   ```

   * You should see a message indicating a successful DNS update.

7. **Log in to Nginx Proxy Manager.**

   * Open a web browser and go to `http://<your-server-ip>:81`.

   * Log in with the default credentials:

     * **Email:** `admin@example.com`

     * **Password:** `changeme`

   * **⚠️ WARNING:** **Immediately** change your login credentials for security.

8. **Add your SSL Certificate.**

   * In the Nginx Proxy Manager dashboard, click on **SSL Certificates**.

   * Click **Add SSL Certificate**.

   * Add your domain and a wildcard domain (e.g., `yourdomain.com` and `*.yourdomain.com`).

   * Check "Use a DNS Challenge" and select your provider.

   * Enter your API token and save.

9. **Create a Proxy Host to test.**

   * Click on **Proxy Hosts**.

   * Add a new proxy host.

   * For the domain, add your root domain (e.g., `hello.yourdomain.com`).

   * For the destination, add `<yourip>` and the port of the `helloworld` container (which is `8888` as defined in your `compose.yml`).
  
   * Enable `Websocket support` and `Block Common Exploits`

   * Go to the **SSL** tab, select the certificate you just created, and check all the boxes: "Force SSL," "HTTP/2 Support," "HSTS Subdomains," and "HSTS Enabled."

   * Click **Save**. You can now test it by navigating to your domain in a web browser.

10. **Customizing for specific apps.**

    * For apps like Jellyfin, you'll need to configure their internal networking to work with Nginx Proxy Manager.

    * Go to your app's networking settings and change the known proxy to the IP of your Nginx Proxy Manager.

    * **⚠️ WARNING:** If you plan to open Jellyfin to the worldwide web, you must follow the official Jellyfin documentation for Nginx setup, as it requires custom settings.

    * You may also need to enable WebSocket support in the advanced settings of your proxy host.
      
11. **Using subdomains.**

    * You can use subdomains with the custom location feature in NGIX.
   
## Apps That Require a Specific Set Up:
---

* For Qbit:
  * Paste the following in advanced:
    ```bash
    proxy_set_header Host $proxy_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Host $http_host;
    proxy_set_header X-Forwarded-Proto $scheme; 
    ```
  * In Qbit go Settings -> WebUI:
    * Check enable reverse proxy support:
      * Add your proxies IP
      * Verify All boxes are checked for Security
      * Save and Retest and make sure you can connect via your proxy url
      * Enable Host header validation and input your server domain
        * EX: qbit.example.com
      * Save
* For NZBGET:
  * got advanced in ngnix and paste the following:
    ```bash
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Host $host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Real-IP $remote_addr;
    ```
Layout: [Layout](../Layout)
Next: [Torrent/UseNet](../TorrentUseNet)
## 🐳 Installation and Setup Guide

### 📂 Step 1: Directory Setup

1. Create or navigate to your desired directory to store the Docker files.

   ```
   sudo mkdir torrentusenet
   cd torrentusenet
   ```

2. Give your user read and write permissions for this directory.

### ⚙️ Step 2: Docker Files

3. Pull the `docker-compose.yml` and `.env` files for the torrent/usenet stack.
   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/TorrentUseNet/.env
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/TorrentUseNet/compose.yml
   ```

5. Change all the placeholder values `<>` in both the `docker-compose.yml` and `.env` files.

### 🚀 Step 3: Running the Containers
* If running on lxc navigate to etc/pve/lxc/105.conf and add
```bash
lxc.cgroup2.devices.allow: c 10:200 rwm
lxc.mount.entry: /dev/net dev/net none bind,create=dir
lxc.mount.entry: /dev/net/tun dev/net/tun none bind,create=file
```

5. Run the Docker Compose command to start all services in the background.

   ```
   docker compose up -d
   ```

6. Check the logs of all Docker containers to ensure they started correctly.

   ```
   docker compose logs
   ```

### 🔐 Step 4: VPN and IP Verification (Gluetun)

7. Verify your VPN connection by running a command to check your public IP.

   ```
   docker run --rm --network=container:gluetun alpine:3.18 sh -c "apk add wget && wget -qO- https://ipinfo.io"
   ```

   Alternatively, you can access the Gluetun container's shell and run the command from there.

   ```
   docker exec -it gluetun bash
   wget -qO- https://ipinfo.io
   ```

### 🔧 Step 5: Configuring qBittorrent

8. Access qBittorrent at `http://<your-server-ip>:8080`.

9. Get the default login password from the Docker logs of the qBittorrent container.

10. Go to `Settings` -> `Web UI` and change the default password.

11. Restart the qBittorrent container and log in with your new credentials.

12. Go to `Settings` -> `Connections` and verify the correct port is being used.

13. In `Settings` -> `Advanced`, change the network interface to `tun0` and save.

14. In `Settings` -> `Downloads`, change the default save path, incomplete path, and `.torrent` file path.

15. Test by copying a torrent link, like a Linux distribution ISO.

### ⚙️ Step 6: Configuring NZBget

16. Log in to NZBget at `http://<your-server-ip>:6789` with the default username `nzbget` and password `tegbzn6789`.

17. Go to `Settings` and change your username and password, then save and relogin.

18. Go to `Settings` -> `Incoming NZBs` and turn off `AppendCategoryDir`.

19. In `Settings` -> `Paths`, change the main destination and intermediate directory to your preferred paths.



Layout: [Layout](../Layout)
## ➡️ Other Software - Check out my docker-files too see how i've set these apps up.
#### Here is a list of applications that did not necessarily need a full guide. - The reason for this is because apps constantly change, and it is more efficient to check there documentation.
* Glance: Dashboard for homeserver. Great documentation with real time backup.
    * Docker-file is up to date with my latest config.

* Immich: Photo management
    * Docker-file is my latest config but pulls a older image.

* CyberChef: A great It tool. Simple container.

* Itools: Another great It tool and simple container

* Jellyfin and Jellyseerr: A media streaming app.

* **NetAlert**: Network tool for checking if 

* **Syncthing**: A tool for allowing realtime file syncronization. I use this all the time.

* **Netdata**: A tool for monitoring network data

* **FreshRSS**: A tool for RSS Feeds.

* **Dozzle**: A tool for checking docker logs in the web browser

* **Firefly**: A budget monitor tool.

* **Karakeep**: A bookmark hoarding tool for those kind of people 😁

* **OpenwebUI**: A nice gui for local AI.

* **Reactive Resume**: A resume creator.

* **Uptime Kuma**: A simple gui to see if containers and VMs are running.

* **Wishlist**: A web gui to create a wishlist.

##Here is a list of alternative applications that are not currently in use or are being tested for potential future integration.


* Next Cloud: A great alternative to a cloud feel.
    * I am currently not using this as it has many features that I don't necessarily need for just my self

* **Pangolin**: A reverse proxy

* **Wazuh**: A nice network tool that I have been learning currently.

* **Graylog**: A nice network tool for log management that I have been learning currently.

* **Security Onion**: A full feature network tool. You need a machine with two network cards to run it. So i have been unable to test it.

* **N8N**: A automation tool with AI. Currently setting it up.

* **VaultWarden**

* **Docmost**

* **Authentik**

* **Home Assistant**: Dashboard alternative to glance

* **Metabase**: A data analyizing tool.

* **Invoice Ninja**: A invoice tool. Have had some issues getting it to run in docker because I am not well versed in php.

* **Grafana**

* **InfluxDB**

* **Cockpit**

* **Audiobook Shelf**

* **Truenas**

* **Homarr**

* **Surveillance Station**

* **Xen Orchestra**

* **Apache Guacamole**

* **Frigate with Coral**

* **Twingate**

* **Pi-hole**

* **Portainer.io**

* **OctoPrint**

* **Plex**

* **Intro Skipper**

* **Fanart**

* **Tmbd**

* **Boxsets**

* **TheTVDB**

* **Skinmanager**

* **Media Bar**

* **Apache Guacamole**

* **Draw.io**

* **Linkstack**

* **Vesc One Wheel**

* **Accrescent**

* **Zigbee**

* **KnockKnock**

* **Prometheus**

* **RocketChat**

* **Logseek**

* **Filebrowser**

Next: [Roadmap](../RoadMap)
Layout: [Layout](../Layout)


# 💻 My Personal Desktop Software Guide

This guide is a curated list of software I currently use on my desktop that are not part of my server setup. It includes powerful tools for automation, enhanced productivity, and general use. The goal of this guide is to provide a comprehensive overview of a personal computing ecosystem designed for efficiency and control.

## 🔧Package Management

### Chocolatey

**Chocolatey** is a command-line package manager for Windows that streamlines the process of installing, upgrading, and removing software. By using Chocolatey, you can easily maintain a consistent and up-to-date software environment without the hassle of manual installations. This is a crucial step for anyone looking to build a more efficient workflow.


## 📝 Productivity and Tools

### Zetlr

**Zetlr** is a powerful and intuitive Markdown editor that I use to create and manage all my documents, including this very guide. It's an excellent tool for taking notes, writing articles, and organizing structured content efficiently.

### Todoist

**Todoist** is an application I use for managing my to-do lists and organizing my tasks. It helps me stay on top of my daily responsibilities and long-term goals by providing a clean and effective way to plan my work.

### Other Recommended Software

Here is a more detailed list of other common but essential programs that contribute to a secure and productive desktop environment:

* **Discord:** A flexible communication platform for connecting with communities and friends.

* **Firefox:** A web browser that prioritizes user privacy and offers a robust set of features.

* **YubiKey Software:** An application for managing my YubiKey security keys, providing a strong layer of hardware-based security for my accounts.

* **Bitwarden:** A secure, open-source password manager that simplifies the management of complex passwords.

* **Ublock Origin:** A highly effective ad and content blocker that improves browsing speed and security.

* **Privacy Badger:** An extension from the Electronic Frontier Foundation (EFF) that automatically blocks invisible trackers.

* **Signal:** A private messaging app with end-to-end encryption.

* **Ente Auth:** A secure authenticator app for two-factor authentication.

* **Ear Trumpet:** A Windows-specific volume mixer that offers more granular control than the default system mixer.

* **VoiceMeeter:** A virtual audio mixer for advanced audio routing and mixing, often used by streamers and podcasters.

* **VSCode:** A highly versatile and customizable code editor for a wide range of programming languages and tasks.

* **WizTree:** A powerful and fast disk space analyzer that helps visualize disk usage and identify large files for cleanup.

* **Anki:** A flashcard program that uses spaced repetition to optimize learning and memory retention.

* **Typts**



Layout: [Layout](../Layout)
# Roadmap
    Add netbird guide - need to get docker container to run

    Add invoiceninja guide

    Add n8n Guide

    🧹 Clean up and make guide more structured and fix grammer

    Create a script to make the process more automated 

Layout: [Layout](../layout)


## 🚀 Contributing

If you found this project helpful, please consider contributing.

Here are a few ways to contribute:

* ➡️ Share this project with others.
* ➡️ Help others who are less tech-savvy set up and manage their own homelabs.
* ➡️ Add to this repository with any tweaks you make. Once you get in the habit, this doesn't add much time to your workflow. I document every change I make in a pulled version of this repository, which adds only a few minutes at most to my workflow.
* ➡️ Support the open-source apps used in this project.
* ➡️ Support the references I've included.
* ➡️ Buy me a coffee to allow me to dedicate more time to this and other open-source projects

