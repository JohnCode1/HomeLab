# 🎵 Setting up Metube

## What We Will Be Doing

* In this guide, we will set up **Metube**, a web GUI for `yt-dlp` that allows you to download videos and audio from various websites.

* We will use a `docker-compose.yml` file to run the application as a single container.

## Guide

### 📂 Step 1: Directory Setup

1. **Create a project directory.**

   ```bash
   mkdir metube
   cd metube
   ```

2. **Create the `docker-compose.yml` file.**

   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/metube/compose.yml
   ```

### 🚀 Step 2: Running the Container

3. **Start the container.**
   
   ```
   docker compose up -d
   ```

### ⚙️ Step 3: Accessing the Application

4. **Access the application.**

   * Once the container is running, you can access the Metube web interface by opening a web browser and navigating to your server's IP address on port `8083`.

   * For example, `http://<your-server-ip>:8083`.

Layout: [Layout](../Layout)
Next: [CyberChef](../Cyberchef)

