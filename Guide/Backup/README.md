# 🔄 Setting up Backups
### **Method 1: Manual Backups (Quick & Simple)**

This method is useful for a quick backup or if you have limited resources.

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

1. **Install the Proxmox Backup Server:** Install the Proxmox Backup Server ISO onto a separate VM or physical machine. Recomened giving it 32 GB of memory

   * Give it a name, such as `backup.local`.

   * Select your disk for the OS and storage.

   * Assign the desired number of CPU cores and RAM.

2. **Initial Setup:** Log in to your new Proxmox Backup Server using the web interface and run the promox Community Post install script. Select yes to all except for pbe test


3. **Get the Fingerprint and Configure BackUp Server:**

   * Go to the **`Dashboard`** of your Proxmox Backup Server. EX. 192.168.1.1:8007
  
   * Create a ZFS Pool for your storage set comporession to `lz4`

   * Find and copy the **`Fingerprint`**. This unique ID is a security key used to connect your main Proxmox host to this backup server.

4. **Connect to Your Main Proxmox Host:**

   * Navigate to your **main Proxmox host**'s web interface. 

   * Click on **`Datacenter`** -> **`Storage`**.

   * Click **`Add`** -> **`Proxmox Backup Server`**.

   * Enter the credentials for your backup server.
  
     * Root@pam for username
    
     * Select an id name of your choice
    
     * Enter IP of proxmox back up server
    
     * Datastore is name of server

     * Paste the **`Fingerprint`** you copied earlier 

6. **Configure Backup Job:**

   * Navigate to **`Datacenter`** -> **`Backups`**.

   * Click **`Add`** to create a new backup job.

   * Select the **node** you want to back up.

   * Choose the **Proxmox Backup Server** as the backup destination.

   * Select a **schedule** (e.g., daily, weekly).
  
   * Select VMS to Backup

   * Set the **`Retention`** policy (how many backups to keep).

   * Set the **`Mode`** to **`Snapshot`**.
  
   * Verify Backups enable on disk for vms/containers
  
     * for containers go to resources select disk and ensure backup is checked
    
     * for vms go to hardware click on your disk select advanced and verify backup is checked.

7. **Test the Backup:**

   * To verify everything is working, select your VM or container.

   * Go to the **`Backup`** tab and click **`Backup now`**.

   * Your new backup job should appear in the dropdown. Select it and click `Backup` to run an immediate test.
  
  Next: [Docker](../Docker)
  Layout: [Layout](../Layout)

