# 🛠️ Installing and Setting Up IT Tools

## What We Will Be Doing

* In this guide, we will set up **IT Tools**, a collection of handy offline tools for developers.

* We will use a `docker-compose.yml` file to run the application as a single container.

## Guide

1. **Create a project directory.**

   * First, create a new folder for your IT Tools project. You can name it whatever you like, for example, `it-tools`.

   ```
   mkdir it-tools
   cd it-tools
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `it-tools` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `compose.yml` file you provided into this file.

   * This file defines the `ittools` service, which pulls the necessary Docker image and maps a port for access.

3. **Start the container.**

   * With the `docker-compose.yml` file in place, you can now start the IT Tools container. The `-d` flag runs the container in the background.

   ```
   docker-compose up -d
   ```

4. **Access the application.**

   * Once the container is running, you can access the IT Tools web interface by opening a web browser and navigating to your server's IP address on port `8081`.

   * For example, `http://<your-server-ip>:8081`.

Layout: [Layout](../Layout)
Next: [Torrent/UseNet](../UseNet)
