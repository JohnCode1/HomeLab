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
  ```bash
    wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/freshrss/compose.yml
  ```

3. **Create the `.env` file.**
   * Input IP, email, API Password, and a DB password

   ```
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/freshrss/.env
   ```

5. **Start the containers.**

   * With both files in place, you can now start the Fresh RSS containers. The `-d` flag runs the containers in the background.

   ```
   docker-compose up -d
   ```

6. **Access the application.**

   * Once the containers are running, you can access the Fresh RSS web interface by opening a web browser and navigating to your server's IP address on port `8080`.

   * For example, `http://<your-server-ip>:8080`.

   * On your first visit, you will be guided through a simple setup process to configure your admin user and database connection.
Next: [KaraKeep](../Karakeep)
Layout: [Layout](../Layout)
