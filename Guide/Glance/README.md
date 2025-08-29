# 📂 Installing and Setting Up Glance

## What We Will Be Doing

* In this guide, we will set up **Glance**, a simple and fast self-hosted application for sharing files and streaming media.

* We will use a `docker-compose.yml` file and a `.env` file to configure and run the application.

## Guide

1. **Create a project directory.**

   * First, navigate to where you are storing your dockerfiles whcreate a new folder for your Glance project. 

   ```
   mkdir glance
   cd glance
   ```

2. **Create the docker compose file.**
   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/compose.yml
   ```

3. **Create the `.env` file.**
   
   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/.env
   nano .env
   # Change the secret token by running openssl rand -base64 36 to create one
   # Cntrl^O to save and cntrl^x to exit
   ```
   
4. get the assetts and config files and create folders for them
   ```bash
   mkdir assets
   cd assets
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/assets/user.css
   cd ..
   mkdir config
   cd config
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/config/gaming.yml
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/config/glance.yml
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/config/home.yml
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/glance/config/startpage.yml
   cd ..
   ```

4. **Start the container.**

   * With both files in place, you can now start the Glance container. The `-d` flag runs the container in the background.

   ```
   docker-compose up -d
   ```

5. **Access the application.**

   * Once the container is running, you can access the Glance web interface by opening a web browser and navigating to your server's IP address on port `8000`.

   * For example, `http://<your-server-ip>:8000`.

   * You can now upload files to the `data` folder inside your project directory, and they will automatically appear in the Glance web interface.Next: [Immich](../Immich)
Layout: [Layout](../Layout)
