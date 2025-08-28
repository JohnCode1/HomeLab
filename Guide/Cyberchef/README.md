# 👨‍🍳 Setting up CyberChef

## What We Will Be Doing

* In this guide, we will set up **CyberChef**, a web application for data analysis, encryption/decryption, and more.

* We will use a `docker-compose.yml` file to run the application.

## Guide

### 📂 Step 1: Directory Setup

1. **Create a project directory.**

   * First, create a new folder for your CyberChef project. You can name it whatever you like, for example, `cyberchef-docker`.

   ```
   mkdir cyberchef-docker
   cd cyberchef-docker
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `cyberchef-docker` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `compose.yml` file you provided into this file. This file will define the `cyberchef` service and its port mapping.

### 🚀 Step 2: Running the Container

3. **Start the container.**

   * With the `docker-compose.yml` file in place, you can now start the CyberChef container. The `-d` flag runs the container in the background.

   ```
   docker-compose up -d
   ```

### ⚙️ Step 3: Accessing the Application

4. **Access the application.**

   * Once the container is running, you can access the CyberChef web interface by opening a web browser and navigating to your server's IP address on port `8084`.

   * For example, `http://<your-server-ip>:8084`.
Next: [DesktopPrograms](../DesktopPrograms)
Layout: [Layout](../Layout)
