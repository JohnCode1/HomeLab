# 📸 Installing and Setting Up Immich

## What We Will Be Doing

* In this guide, we will set up **Immich**, a high-performance self-hosted backup solution for your photos and videos.

* We will use a `docker-compose.yml` file to run multiple interconnected services for the application.

## Guide

1. **Create a project directory.**

   * navigate to where you are storing your docker files

   ```
   mkdir immich
   cd immich
   ```

2. **Create the `docker-compose.yml` and `.env` file.**

   * Inside the `immich` directory:
     ```bash
     wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/immich/compose.yml
     wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/immich/.env
     ```

3. **change your ip and create a db password and input it into `.env`: `cntrl^shift^c to copy` `cntrl^o` to save `cntrl^x` to exit**

   ```
   openssl rand -hex 32
   nano .env
   ```

4. **Start the container.**

   * With both files in place, you can now start the Immich containers. The `-d` flag runs the containers in the background.

   ```
   docker compose up -d
   ```

5. **Access the application.**

   * Once the containers are running, you can access the Immich web interface by opening a web browser and navigating to your server's IP address on port `2283`.

   * For example, `http://<your-server-ip>:2283`.

   * The application will prompt you to create an admin user on your first visit.
Next: [FreshRSS](../FreshRSS)
Layout: [Layout](../layout)
