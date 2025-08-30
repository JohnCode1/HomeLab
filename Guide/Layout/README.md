# 📚 Structure of this Guide and How to Use It

* ➡️ This guide provides links at the end of each page to lead you to the next page, allowing you to follow the sections in order.

* 🔄 It is also perfectly fine to follow this guide **out of order** and choose what you want to implement. However, be aware that you may need to make some tweaks depending on where you start.

  * > **Example:** If you do not use the file setup that I have, you will have to adjust your own setup accordingly.

* 🧭 At the end of each page, after the link to the next section, I will include a link to get back to this page for easy navigation.

* ⚙️ After the navigational links, I will list all the additional tweaks and terminal commands I have used in the past but are not currently in use. This allows you to easily find and copy the commands you need without having to constantly scroll.

  * > **Example:** If you follow the guide and later make a mistake, forcing you to restart your server from scratch, you can quickly find the commands you need in this section.
    
* ⚙️ For this guide I will be setting up proxmox. After setting up Proxmox I will then create a Container to use as two samba shares that will house all the media and docker files. After that I will create one VM to run all the apps.
 * NOTE: For apps Next Cloud, Jellyfin, and TorrentUsenet stack you will need to make seperate directories on the VM/Container running those apps to store the docker files. If you store your docker files on a seperate VM/Container for those apps they run into issues currently and do not run properly.
 * NOTE: For extra Security it is recommended to seperate the apps out more to seperate VMS/Containers which if you do this you will just have to create extra VMS/Containers. Just repeat the guide for setting up a container and/or VM then set up docker and/or samba from the guide.
 * NOTE: It is also helpful to make all your containers and vms static ips in your router settings and name them in acordance to the node id of your vm/container
* ⚙️ After setting up the apps use netbird to connect into your apps or an overlay VPN of your choice. I do not have a guide for this yet and is at the bottom of my todo list due to the documentation being very nice and friendly of netbird.

### NEW ADDITIONS: Next cloud and server data monitoring stack. They are not linked along in the guide but you can find links for them at the bottom of this layout

### Next Page: Hardware Selection

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

Next: [Proxmox](../Proxmox)
