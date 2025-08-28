# 📸 Installing and Setting Up Immich

## What We Will Be Doing

* In this guide, we will set up **Immich**, a high-performance self-hosted backup solution for your photos and videos.

* We will use a `docker-compose.yml` file to run multiple interconnected services for the application.

## Guide

1. **Create a project directory.**

   * Create a new folder for your Immich project. This is a good practice to keep all your application files organized. You can name it whatever you like, for example, `immich`.

   ```
   mkdir immich
   cd immich
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `immich` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `immich_compose` immersive above into this file.

   * This file defines all the necessary services for Immich: the database, Redis, the microservices, the server, and the web client.

3. **Create the `.env` file.**

   * Next, create a new file in the same directory and name it `.env`.

   * Copy and paste the contents from the `immich_env` immersive above into this file.

   * **Important:** You need to find your `PUID` and `PGID` and replace the placeholder values (`1000`) with your actual IDs. To find them, open a terminal on your server and run:

   ```
   # To find your PUID
   id -u yourusername

   # To find your PGID
   id -g yourusername
   ```

   * You must also update the `POSTGRES_PASSWORD` and `IMMICH_SERVER_URL` with your own secure credentials and server information.

4. **Start the container.**

   * With both files in place, you can now start the Immich containers. The `-d` flag runs the containers in the background.

   ```
   docker-compose up -d
   ```

5. **Access the application.**

   * Once the containers are running, you can access the Immich web interface by opening a web browser and navigating to your server's IP address on port `2283`.

   * For example, `http://<your-server-ip>:2283`.

   * The application will prompt you to create an admin user on your first visit.
Next: [FreshRSS](../FreshRSS)
Layout: [Layout](../layout)
