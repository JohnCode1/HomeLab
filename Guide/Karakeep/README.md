# 🗂️ Installing and Setting Up Karakeep

## Guide

1. **Create a project directory.**

   ```
   mkdir karakeep
   cd karakeep
   ```

2. **Create the `docker-compose.yml` file.**

   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/karakeep/compose.yml
   ```

4. **Create the `.env` file.**

   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/karakeep/.env
   ```

   * **Important:** You must update the `<Secret>` and `<master_key>` with your own strong, unique passwords.

6. **Start the containers.**

   ```
   docker compose up -d
   ```

7. **Access the application.**

   * Once the containers are running, you can access the Karakeep web interface by opening a web browser and navigating to your server's IP address on port `3001`.

   * For example, `http://<your-server-ip>:3001`.

   * You will be able to create a user and start adding your bookmarks and snippets.
Next: [ItTools](../ItTools)
Layout: [Layout](../Layout)
