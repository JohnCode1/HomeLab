# 👨‍🍳 Setting up CyberChef

1. **Create a project directory.**

   ```bash
   mkdir cyberchef
   cd cyberchef
   ```

2. **Create the `docker-compose.yml` file.**
  ```bash
  wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/cyberchef/compose.yml
  ```

3. **Start the container.**

   * With the `docker-compose.yml` file in place, you can now start the CyberChef container. The `-d` flag runs the container in the background.

   ```
   docker compose up -d
   ```

4. **Access the application.**

   * Once the container is running, you can access the CyberChef web interface by opening a web browser and navigating to your server's IP address on port `8084`.

   * For example, `http://<your-server-ip>:8084`.
Next: [DesktopPrograms](../DesktopPrograms)
Layout: [Layout](../Layout)
