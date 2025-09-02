# 🌐 Setting up Nginx Proxy Manager
* Warning you are now entering a area where small things matter. Depending on your network set up you may have to change things around.

## What We Will Be Doing

* In this section, we will use **Nginx Proxy Manager** 

* The Nginx Proxy Manager container will act as a reverse proxy, handling all incoming web traffic and routing it to the correct app (like Jellyfin).


## **Guide**

1. **Obtain a domain name.** Go to a domain provider of your choice (like Cloudflare) and purchase a domain name. **⚠️ WARNING:** Make sure the TLD (e.g., `.us` or `.net`) allows for masking your information to prevent spam.

2. **Configure DNS records.** In your DNS provider's settings, add the following records:

   * **Type A record:** with the name `@` and your public IP address.

   * **Type CNAME record:** with the name `*` and your domain name.

   * **Important:** Disable the proxy feature on the DNS provider. This is crucial for self-hosted apps, especially streaming services like Jellyfin, to avoid violating terms of service.
  
   * * **Important:** if you have a firewall or router that suports host or dns over ride use that instead. 

3. **Get a Cloudflare API Token.**

   * Go to your profile and create a new API token.

   * Use the "Edit zone DNS" template.

   * Include all zones, then continue to the summary and copy the API token.

4. **Run the containers.**

   * Navigate to the directory where your storing your docker files and mkdir for ngix.
     ```bash
     mkdir ngix
     cd ngix
     wget https://raw.githubusercontent.com/JohnCode1/HomeLab/refs/heads/main/docker/nginx/compose.yml
     ``` 

   * Run the following command to start the containers in the background:

   ```bash
   docker compose up -d
   ```

5. **Verify the containers are running.**

   ```bash
   docker compose logs
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

9. **Create a Proxy Host to test.**

   * Click on **Proxy Hosts**.

   * Add a new proxy host.

   * For the domain, add your root domain (e.g., `hello.yourdomain.com`).

   * For the destination, add `<yourip>` and the port of the `helloworld` container (which is `8888` as defined in your `compose.yml`).
  
   * Enable `Websocket support` and `Block Common Exploits`

   * Go to the **SSL** tab, select the certificate you just created, and check all the boxes: "Force SSL," "HTTP/2 Support," "HSTS Subdomains," and "HSTS Enabled."

   * Click **Save**. You can now test it by navigating to your domain in a web browser.

10. **Customizing for specific apps.**

    * For apps like Jellyfin, you'll need to configure their internal networking to work with Nginx Proxy Manager.

    * Go to your app's networking settings and change the known proxy to the IP of your Nginx Proxy Manager.

    * **⚠️ WARNING:** If you plan to open Jellyfin to the worldwide web, you must follow the official Jellyfin documentation for Nginx setup, as it requires custom settings.

    * You may also need to enable WebSocket support in the advanced settings of your proxy host.
      
11. **Using subdomains.**

    * You can use subdomains with the custom location feature in NGIX.
   
## Apps That Require a Specific Set Up:
---

* For Qbit:
  * Paste the following in advanced:
    ```bash
    proxy_set_header Host $proxy_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Host $http_host;
    proxy_set_header X-Forwarded-Proto $scheme; 
    ```
  * In Qbit go Settings -> WebUI:
    * Check enable reverse proxy support:
      * Add your proxies IP
      * Verify All boxes are checked for Security
      * Save and Retest and make sure you can connect via your proxy url
      * Enable Host header validation and input your server domain
        * EX: qbit.example.com
      * Save
* For NZBGET:
  * got advanced in ngnix and paste the following:
    ```bash
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Host $host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Real-IP $remote_addr;
    ```
Next: [Windows VM](../WindowsVM)
Layout: [Layout](../Proxmox)

