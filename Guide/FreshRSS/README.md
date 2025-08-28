# 📰 Installing and Setting Up Fresh RSS

## What We Will Be Doing

* In this guide, we will set up **Fresh RSS**, a free, self-hosted RSS feed aggregator that you can use to read all your favorite blogs and news sites in one place.

* We will use a `docker-compose.yml` file to run both the Fresh RSS web application and its database.

## Guide

1. **Create a project directory.**

   * First, create a new folder for your Fresh RSS project. You can name it whatever you like, for example, `freshrss`.

   ```
   mkdir freshrss
   cd freshrss
   ```

2. **Create the `docker-compose.yml` file.**

   * Inside the `freshrss` directory, create a new file named `docker-compose.yml`.

   * Copy and paste the contents from the `fresh_rss_compose` immersive above into this file.

   * This file defines the two necessary services: a MariaDB database and the Fresh RSS application itself.

3. **Create the `.env` file.**

   * Next, create a new file in the same directory and name it `.env`.

   * Copy and paste the contents from the `fresh_rss_env` immersive above into this file.

   * **Important:** You must update the `MYSQL_ROOT_PASSWORD`, `FRESHRSS_DB_PASS`, `PUID`, and `PGID` with your own secure credentials and IDs.

   * To find your `PUID` and `PGID`, open a terminal on your server and run:

   ```
   # To find your PUID
   id -u yourusername

   # To find your PGID
   id -g yourusername
   ```

4. **Start the containers.**

   * With both files in place, you can now start the Fresh RSS containers. The `-d` flag runs the containers in the background.

   ```
   docker-compose up -d
   ```

5. **Access the application.**

   * Once the containers are running, you can access the Fresh RSS web interface by opening a web browser and navigating to your server's IP address on port `8080`.

   * For example, `http://<your-server-ip>:8080`.

   * On your first visit, you will be guided through a simple setup process to configure your admin user and database connection.
Next: [KaraKeep](../Karakeep)
Layout: [Layout](../Layout)
