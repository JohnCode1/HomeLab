# 📊 Setting Up Server Monitoring

This guide will walk you through setting up a server monitoring stack using **Grafana** for visualization, **Prometheus** and **InfluxDB** for data storage, and **Telegraf** and **Prometheus Node Exporter** for data collection.

> ⚠️ **Warning:** The following setup is not currently secured and should only be run on a server that is not open to the public web.

## 💻 Installation and Configuration

### Step 1: Prepare the VM

1. Create a new Ubuntu virtual machine.

2. Install the Prometheus Node Exporter to expose system metrics.

   ```
   sudo apt install prometheus-node-exporter
   ```

3. Verify that the service is running.

   ```
   sudo systemctl status prometheus-node-exporter
   ```

4. Set up Docker on this VM if you have not already.

### Step 2: Set Up Docker Compose Files

1. Clone the required repository from GitHub.

   ```
   git clone https://github.com/TechHutTv?server-monitoring.git
   ```

2. Navigate into the new directory.

   ```
   cd server-monitoring
   ```

3. Edit the `docker-compose.yml` file to change the hostname.

   ```
   nano docker-compose.yml
   ```

4. Change the `extra_hosts` to your server's hostname.

5. Save the file (`Ctrl + O`) and exit (`Ctrl + X`).

### Step 3: Configure Prometheus

1. Edit the `prometheus.yml` file.

   ```
   nano prometheus.yml
   ```

2. Change the `targets` to your specific server IP addresses and ports.

3. Save the file (`Ctrl + O`) and exit (`Ctrl + X`).

### Step 4: Update Host File

1. Edit the system hosts file.

   ```
   sudo nano /etc/hosts
   ```

2. Add a new section for custom hostnames.

   ```
   # Custom Hostnames
   ```

3. Add your IPs and hostnames to the file.

4. Save the file and reboot the server to apply the changes.

   ```
   sudo reboot
   ```

### Step 5: Start the Monitoring Stack

1. Navigate back to the `server-monitoring` directory and start the Docker containers.

   ```
   docker compose up -d
   ```

2. Check the logs of the running containers to ensure there are no errors.

   ```
   docker compose logs
   ```

## 📈 Setting Up Grafana and InfluxDB

### Step 6: Configure InfluxDB

1. Navigate to your browser and go to the InfluxDB web interface on port `8086`.

   ```
   http://<your-vm-ip>:8086
   ```

2. Create a new account.

3. Set the bucket name to `influxdb`.

4. Copy the generated API token, as you will need it later.

### Step 7: Configure Grafana

1. Go to your browser and access Grafana on port `3000`.

   ```
   http://<your-vm-ip>:3000
   ```

2. Log in with the default credentials: `admin` and `admin`.

3. Change your login credentials immediately.

4. Add Prometheus as a data source and test the connection.

### Step 8: Connect InfluxDB to Grafana

1. Add a new data source in Grafana.

2. Select **InfluxDB** from the list.

3. Set the name to `Proxmox`.

4. Choose the `InfluxQL` language.

5. Set the URL to `http://influxdb:8086`.

6. Check `Skip TLS Verify`.

7. Set the database name to `influxdb`.

8. Use your copied API token as the password.

9. Set the HTTP method to `GET`.

### Step 9: Import Dashboards

1. For the Node Exporter metrics, import the **Grafana Node Exporter Full** dashboard.

2. Set the data source for this dashboard to **Prometheus**.

3. For Proxmox monitoring, import dashboard **10048** and set the source to `Proxmox` (the name you gave the InfluxDB data source).

## 🐳 Monitoring Docker and Proxmox

### Step 10: Configure Telegraf for Docker

1. Edit the Telegraf configuration file.

   ```
   nano telegraf/telegraf.conf
   ```

2. Paste in your InfluxDB API token.

3. Add your InfluxDB organization and bucket name.

4. Add a new Grafana connection for Telegraf.

5. Set the query language to `Flux`.

6. Turn off basic authentication and check `Skip TLS Verify`.

7. Paste in your token and bucket.

8. Import the **Grafana 18389** dashboard to visualize Docker metrics.

### Step 11: Configure InfluxDB on Proxmox

1. Go to the Proxmox web interface.

2. Navigate to **Datacenter** -> **Metrics Server**.

3. Add a new InfluxDB server.

4. Give it a name.

5. Enter the IP address of the server running InfluxDB.

6. Set the protocol to `HTTP` and the port to `8086`.

7. Enter the bucket as `proxmox`.

8. Paste in your InfluxDB API token.
