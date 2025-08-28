# 📂 Installing and Setting Up Glance

## What We Will Be Doing

* In this guide, we will set up **Glance**, a simple and fast self-hosted application for sharing files and streaming media.

* We will use a `docker-compose.yml` file and a `.env` file to configure and run the application.

## Guide

1. **Create a project directory.**

   * First, create a new folder for your Glance project. This is a good practice to keep all your application files organized. You can name it whatever you like, for example, `glance`.

   ```
   mkdir glance
   cd glance
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `glance` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `glance_compose` immersive above into this file.

   * This file defines the `glance` service, its Docker image, ports, and data volume.

3. **Create the `.env` file.**

   * Next, create a new file in the same directory and name it `.env`.

   * Copy and paste the contents from the `glance_env` immersive above into this file.

   * **Important:** You need to find your `PUID` and `PGID` and replace the placeholder values (`1000`) with your actual IDs. To find them, open a terminal on your server and run:

   ```
   # To find your PUID
   id -u yourusername

   # To find your PGID
   id -g yourusername
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
