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

# 🔗 Connecting to the Samba Share

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

17. Change the ownership of the mounted directories:

    ```
    sudo chown -R 1000:1000 /<path1>
    sudo chown -R 1000:1000 /<path2>
    ```

# 📁 Creating File Paths

* Use the following commands to create the file paths that will be used for future applications in this guide:

```
mkdir -p downloads/qbittorrent/{completed,incomplete,torrents} && mkdir -p downloads/nzbget/{completed,intermediate,nzb,queue,tmp} && mkdir -p books/ && mkdir -p movies && mkdir -p music && mkdir -p shows && mkdir -p youtube
```

Next: [Backup](../Backup) Layout: [Layout](../Layout)
