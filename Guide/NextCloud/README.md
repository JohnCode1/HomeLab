**WARNING Current issues with running dockerfile via samaba and setting up initial storage via samba. Can connect to samba after inital set up.

### Nextcloud Setup Guide

This section provides a step-by-step guide for setting up Nextcloud on a Docker-enabled virtual machine.

1. **Create a Directory:** Make a new directory to store all your Nextcloud docker files.

   ```
   mkdir nextclouddocker
   ```

2. **Set Permissions:** Give your user the correct permissions for the new directory and make a directory to store the data.

   ```
   sudo chown -R 1000:1000 /nextclouddocker/
   mkdir ncdata
   ```

3. **Pull the Docker File:** Download the necessary Docker Compose file.

   ```
   wget <your-docker-compose-file-url>
   ```

4. **Start the Container:** Run the Docker Compose file to start the Nextcloud container in the background.

   ```
   docker compose up -d
   ```

5. **Check Logs:** Monitor the container logs to ensure it's running correctly.

   ```
   docker logs nextcloud
   ```

6. **Access Nextcloud:** Go to your web browser and navigate to the IP address of your VM with the port.

   ```
   http://<your-vm-ip>:8088
   ```
* If you loose your password execute the following
  ```bash
  docker exec nextcloud-aio-mastercontainer grep password /mnt/docker-aio-config/data/configuration.json
  ```
7. **Set Up Nginx Proxy:** Configure Nginx to proxy Nextcloud for a secure connection or the proxy manager of your choice. Add a new Proxy Host with the following settings:

   * **Name:** `nextcloud.yourdomain.com` (or your preferred subdomain)
  
   *  **PORT:** `11000` (or your preferred subdomain)

   * **Scheme:** `https`

   * **Block Common Exploits:** Enable this option.

   * **Websockets Support:** Enable this option.

   * **SSL:** Check the top all boxes.

   * **Custom Locations:** Add a new custom location with the following pasted in the body:

     ```
     client_body_buffer_size 512k;
     proxy_read_timeout 86400s;
     client_max_body_size 0;
     ```

8. **Complete Nextcloud AIO Setup:**

   * Go to the Nextcloud AIO interface and submit your domain.
  
   * If you have the RAM check `fulltextsearch and clamav`

   * Read through and select any other options you want.
      * I have: CLAMAV, COLLABORA, FULLTEXTSEARCH, IMAGINARY, WHITEBOARD, 
     
   * Copy the default login credentials and log in to Nextcloud.

   * Go to "Accounts" to change your display name, password, and email.
  
   * Go to Admin Settings and check for issues
