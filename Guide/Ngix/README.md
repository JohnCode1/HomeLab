# 🌐 Setting up Nginx Proxy Manager

## What We Will Be Doing

* In this section, we will use **Nginx Proxy Manager** and a **Dynamic DNS (DDNS)** updater to expose your self-hosted apps securely to the internet.

* The Nginx Proxy Manager container will act as a reverse proxy, handling all incoming web traffic and routing it to the correct app (like Jellyfin).

* The DDNS container will automatically update your domain's DNS record with your home's public IP address, ensuring your domain always points to the correct location.

## **Guide**

1. **Obtain a domain name.** Go to a domain provider of your choice (like Cloudflare) and purchase a domain name. **⚠️ WARNING:** Make sure the TLD (e.g., `.us` or `.net`) allows for masking your information to prevent spam.

2. **Configure DNS records.** In your DNS provider's settings, add the following records:

   * **Type A record:** with the name `@` and your public IP address.

   * **Type CNAME record:** with the name `*` and your domain name.

   * **Important:** Disable the proxy feature on the DNS provider. This is crucial for self-hosted apps, especially streaming services like Jellyfin, to avoid violating terms of service.

3. **Get a Cloudflare API Token.**

   * Go to your profile and create a new API token.

   * Use the "Edit zone DNS" template.

   * Include all zones, then continue to the summary and copy the API token.

4. **Edit your `docker-compose.yml` file.**

   * Open your `compose.yml` file.

   * Locate the `ddns` service.

   * Replace `<API Token>` with the API token you just copied.

   * For the `<domains>` section, you will need to add two entries: your main domain (e.g., `yourdomain.com`) and a wildcard entry for subdomains (e.g., `*.yourdomain.com`). This ensures that your DDNS service updates both.

5. **Run the containers.**

   * Navigate to the directory where your `compose.yml` file is located.

   * Run the following command to start the containers in the background:

   ```
   docker-compose up -d
   ```

6. **Verify the containers are running.**

   * Check the logs to ensure the DDNS container is updating your IP correctly:

   ```
   docker-compose logs -f ddns
   ```

   * You should see a message indicating a successful DNS update.

7. **Log in to Nginx Proxy Manager.**

   * Open a web browser and go to `http://<your-server-ip>:81`.

   * Log in with the default credentials:

     * **Email:** `admin@example.com`

     * **Password:** `changeme`

   * **⚠️ WARNING:** **Immediately** change your login credentials for security.

8. **Add your SSL Certificate.**

   * In the Nginx Proxy Manager dashboard, click on **SSL Certificates**.

   * Click **Add SSL Certificate**.

   * Add your domain and a wildcard domain (e.g., `yourdomain.com` and `*.yourdomain.com`).

   * Check "Use a DNS Challenge" and select your provider.

   * Enter your API token and save.

9. **Create a Proxy Host.**

   * Click on **Proxy Hosts**.

   * Add a new proxy host.

   * For the domain, add your root domain (e.g., `yourdomain.com`).

   * For the destination, add `127.0.0.1` and the port of the `helloworld` container (which is `8888` as defined in your `compose.yml`).

   * Go to the **SSL** tab, select the certificate you just created, and check all the boxes: "Force SSL," "HTTP/2 Support," "HSTS Subdomains," and "HSTS Enabled."

   * Click **Save**. You can now test it by navigating to your domain in a web browser.

10. **Customizing for specific apps.**

    * For apps like Jellyfin, you'll need to configure their internal networking to work with Nginx Proxy Manager.

    * Go to your app's networking settings and change the known proxy to the IP of your Nginx Proxy Manager.

    * **⚠️ WARNING:** If you plan to open Jellyfin to the worldwide web, you must follow the official Jellyfin documentation for Nginx setup, as it requires custom settings.

    * You may also need to enable WebSocket support in the advanced settings of your proxy host.
Next: [Windows VM](../WindowsVM)
Layout: [Layout](../Proxmox)
11. **Using subdomains.**

    * You can use subdomains with the custom location feature in NGIX.

