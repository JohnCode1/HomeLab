# 🔄 Setting up Backups

Backing up your data is crucial. This guide provides two methods: a simple manual approach and a more robust, long-term solution using Proxmox Backup Server.

### **Method 1: Manual Backups (Quick & Simple)**

This method is useful for a quick backup or if you have limited resources. It creates a snapshot of your virtual machine (VM) or container at a specific point in time.

1. Navigate to the VM or container you want to back up.

2. Click the **`Backup`** tab.

3. Click **`Backup now`**.

4. For the `Mode` setting, select **`Snapshot`**. This will create a snapshot of your VM.

5. Click **`Backup`** to start the process.

### **Method 2: Using a Dedicated Proxmox Backup Server (Recommended)**

This is the recommended approach for a more professional and reliable setup. A dedicated backup server allows for scheduled backups, efficient data deduplication, and a centralized location for all your backup files.

#### **Software Requirements**

You will need the Proxmox Backup Server ISO image. You can download this from the official Proxmox website.

#### **Guide**

1. **Install the Proxmox Backup Server:** Install the Proxmox Backup Server ISO onto a separate VM or physical machine.

   * Give it a name, such as `backup.local`.

   * Select your disk for the OS and storage.

   * Assign the desired number of CPU cores and RAM.

2. **Initial Setup:** Log in to your new Proxmox Backup Server using the web interface and run the promox Community Post install script. Select yes to all except for pbe test

3. **Create a ZFS Pool:**

   * Navigate to **`Storage / Disks`** in the left-hand menu.

   * Click **`ZFS`** to create a new storage pool. A **ZFS pool** is a powerful file system that provides features like snapshots and data integrity.

   * Set the compression to **`lz4`**.

4. **Get the Fingerprint:**

   * Go to the **`Dashboard`** of your Proxmox Backup Server.

   * Find and copy the **`Fingerprint`**. This unique ID is a security key used to connect your main Proxmox host to this backup server.

5. **Connect to Your Main Proxmox Host:**

   * Navigate to your **main Proxmox host**'s web interface.

   * Click on **`Datacenter`** -> **`Storage`**.

   * Click **`Add`** -> **`Proxmox Backup Server`**.

   * Enter the credentials for your backup server.

   * Paste the **`Fingerprint`** you copied earlier to securely link the two systems.

6. **Configure Backup Job:**

   * Navigate to **`Datacenter`** -> **`Backups`**.

   * Click **`Add`** to create a new backup job.

   * Select the **node** you want to back up.

   * Choose the **Proxmox Backup Server** as the backup destination.

   * Select a **schedule** (e.g., daily, weekly).

   * Set the **`Retention`** policy (how many backups to keep).

   * Set the **`Mode`** to **`Snapshot`**.

7. **Test the Backup:**

   * To verify everything is working, select your VM or container.

   * Go to the **`Backup`** tab and click **`Backup now`**.

   * Your new backup job should appear in the dropdown. Select it and click `Backup` to run an immediate test.
