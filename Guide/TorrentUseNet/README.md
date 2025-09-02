# ⚠️ WARNING: I DO NOT CONDONE PIRACY OR ILLEGAL DOWNLOADS. THIS GUIDE IS FOR EDUCATIONAL PURPOSES ONLY.

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

### 🔄 Step 7: Configuring Prowlarr

20. Log in to Prowlarr at `http://<your-server-ip>:9696`.

21. Select `Forms` authentication, create a username and password, and save.

22. Add your preferred indexers.

23. In `Settings` -> `Download Clients`, add NZBget. Change the host to your Gluetun container's IP (`10.0.0.2` by default), enter your NZBget username and password, and choose a default category.

### 🎬 Step 8: Configuring the Arr Apps (Sonarr, Radarr, Lidarr, Bazarr)

* The setup for these applications is similar and can be done at the same time.

24. Log in to each app using its respective port. For example, Radarr is on port `7878`, and Sonarr is on `8989`.

25. Create a username and password.

26. Go to `Settings` -> `General` and copy the API key.

27. In Prowlarr, go to the `Settings` for the app you are setting up and enter the API key and the IP address of that host.

28. After setting up all the apps, go to `Movies` in Radarr or `Series` in Sonarr and import your existing media from your data directory.

29. In `Settings`, add your download clients.

30. Test the setup by searching for a movie or show you can obtain legally and downloading it.


Next: [Jellyfin](../Jellyfin)
Layout: [Layout](../Layout)
