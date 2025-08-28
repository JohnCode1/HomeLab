# 🎵 Setting up Metube

## What We Will Be Doing

* In this guide, we will set up **Metube**, a web GUI for `yt-dlp` that allows you to download videos and audio from various websites.

* We will use a `docker-compose.yml` file to run the application as a single container.

## Guide

### 📂 Step 1: Directory Setup

1. **Create a project directory.**

   * First, create a new folder for your Metube project. You can name it whatever you like, for example, `metube-docker`.

   ```
   mkdir metube-docker
   cd metube-docker
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `metube-docker` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `compose(1).yml` file you provided into this file.

   * **Note:** You will need to change the volume path `<path/to/downloads>` to the actual path on your server where you want to store the downloaded videos.

### 🚀 Step 2: Running the Container

3. **Start the container.**

   * With the `docker-compose.yml` file in place, you can now start the Metube container. The `-d` flag runs the container in the background.

   ```
   docker-compose up -d
   ```

### ⚙️ Step 3: Accessing the Application

4. **Access the application.**

   * Once the container is running, you can access the Metube web interface by opening a web browser and navigating to your server's IP address on port `8083`.

   * For example, `http://<your-server-ip>:8083`.

Layout: [Layout](../Layout)
Next: [CyberChef](../Cyberchef)

