# 🍿 Setting up Jellyfin and Jellyseerr

## What We Will Be Doing

* In this guide, we will set up **Jellyfin**, a free software media system, and **Jellyseerr**, a platform for managing requests for new media.

* We will use a `docker-compose.yml` file to run both applications.

## Guide

### 📂 Step 1: Directory Setup

1. Go into or create the directory where you will store the Docker files for Jellyfin.

   ```
   mkdir jellyfindocker
   cd jellyfindocker
   ```

2. Pull the `docker-compose.yml` file.

   ```
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/main/docker/jellyfin/compose.yml
   ```

3. Edit the `compose.yml` file to update the paths for your configuration and data files.

   * If you are not using Intel Quick Sync for hardware transcoding, you should also remove the `devices` section.

   ```
   nano compose.yml
   ```

4. Save the file by pressing `Ctrl + O` and exit with `Ctrl + X`.

### 🚀 Step 2: Running the Containers

5. Run the Docker Compose command to start the containers in the background.

   ```
   docker-compose up -d
   ```

6. After the containers are running, check the logs to ensure they started correctly.

   ```
   docker logs jellyfin
   docker logs jellyseerr
   ```

### ⚙️ Step 3: Initial Setup

7. Navigate to your browser and access Jellyfin at `http://<your-server-ip>:8096`.

8. Follow the initial setup wizard:

   * Select your language.

   * Create a username and password.

   * Add your media library by specifying the type of media and the path where your media is stored.

   * Choose your language and region settings.

   * Check the option to enable auto port mapping (if needed).

   * Click `Finish` and log in with your new credentials.

9. Verify that Jellyfin has the proper permissions to access your media by trying to delete a piece of test data. **WARNING: Make sure you have a backup of this data.**

### 🖥️ Step 4: Enabling Hardware Transcoding

10. If you are using Intel Quick Sync for hardware transcoding, go to the Jellyfin dashboard.

    * Click the three bars on the left -> `Dashboard` -> `Playback` -> `Transcoding`.

    * Select the hardware acceleration type you are using.

    * Paste the device path `/dev/dri/renderD128` into the text box below.

    * Save the settings.

11. To check if transcoding is working, you can run the following command on your server to monitor the GPU usage while a video is playing.

    ```
    sudo intel_gpu_top
    ```

### 🔄 Step 5: Configuring Jellyseerr

12. Access Jellyseerr at `http://<your-server-ip>:5055`.

13. Log in and sync your libraries.

14. Scan and add Radarr and Sonarr by providing their IP addresses, ports, and API keys.

15. Update your quality profiles and root folder settings, and change the minimum availability to `Released`.

Next: [Metube](../Metube)
Layout: [Layout](../Layout)
