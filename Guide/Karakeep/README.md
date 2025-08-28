# 🗂️ Installing and Setting Up Karakeep

## What We Will Be Doing

* In this guide, we will set up **Karakeep**, a self-hosted bookmark and snippet manager.

* We will use a `docker-compose.yml` file to run the web application, a headless Chrome instance for rendering web pages, and MeiliSearch for fast search capabilities.

## Guide

1. **Create a project directory.**

   * First, create a new folder for your Karakeep project. You can name it whatever you like, for example, `karakeep`.

   ```
   mkdir karakeep
   cd karakeep
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `karakeep` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `compose.yml` file you provided into this file.

   * This file defines all the necessary services for Karakeep: the `web` application, `chrome` for page rendering, and `meilisearch` for the search database.

3. **Create the `.env` file.**

   * Next, create a new file in the same directory and name it `.env`.

   * Copy and paste the contents from the `.env` file you provided into this file.

   * **Important:** You must update the `<Secret>` and `<master_key>` with your own strong, unique passwords.

4. **Start the containers.**

   * With both files in place, you can now start the Karakeep containers. The `-d` flag runs the containers in the background.

   ```
   docker-compose up -d
   ```

5. **Access the application.**

   * Once the containers are running, you can access the Karakeep web interface by opening a web browser and navigating to your server's IP address on port `3001`.

   * For example, `http://<your-server-ip>:3001`.

   * You will be able to create a user and start adding your bookmarks and snippets.
Next: [ItTools](../ItTools)
Layout: [Layout](../Layout)
