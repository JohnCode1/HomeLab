# 🛠️ Installing and Setting Up IT Tools

## Guide

1. **Create a project directory.**

   ```bash
   mkdir it-tools
   cd it-tools
   ```

2. **Create the `docker-compose.yml` file.**
   
  ```bash
  wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/ittools/compose.yml
  ```
  
3. **Start the container.**
   
   ```bash
   docker compose up -d
   ```

5. **Access the application.**

   * Once the container is running, you can access the IT Tools web interface by opening a web browser and navigating to your server's IP address on port `8081`.

   * For example, `http://<your-server-ip>:8081`.

Layout: [Layout](../Layout)
Next: [Torrent/UseNet](../TorrentUseNet)
