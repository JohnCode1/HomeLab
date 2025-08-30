# 🐳 Installing Docker

## 💻 Installation Steps

Follow these steps to install Docker on your system. These commands will download and install Docker and then set up your user account to use it without needing `sudo` every time.

1. **Download the Docker installation script.** This command uses `curl` to download the official Docker installation script and saves it as `get-docker.sh` in your current directory.

   ```
   curl -fsSL https://get.docker.com -o get-docker.sh
   ```

2. **Run the installation script.** The `sudo sh` command runs the script with administrative privileges, which is required to install Docker and all its dependencies.

   ```
   sudo sh get-docker.sh
   ```

3. **Verify that Docker is running.** After the installation, you can use `systemctl` to check the status of the Docker service. Look for the word `active` in the output to confirm it's running correctly. `cntrl^c` to exit

   ```
   sudo systemctl status docker
   ```

4. **Create the Docker group.** This step creates a special user group called `docker`. This group is a key part of the setup, as it will allow your user to run Docker commands without needing `sudo` every time.

   ```
   sudo groupadd docker
   ```

5. **Add your user to the Docker group.** This command adds your current user (`$USER`) to the newly created `docker` group. This is what enables you to run Docker commands without root privileges.

   ```
   sudo usermod -aG docker $USER
   ```

6. **Activate the new group changes.** The changes to your user's group membership won't take effect immediately. You can either log out and log back in, or you can run this command to refresh the group permissions in your current shell.

   ```
   newgrp docker
   ```

7. **Remove the installation script.** Once Docker is installed, you no longer need the installation script. This is a good practice to keep your system clean.

   ```
   rm get-docker.sh
   ```

   To be extra sure of the file name before removing it, you can run `ls` to list the files in your current directory.
**NOTE:
For apps jellyfin, nextcloud, and QbitUsenet the docker files must be stored locally on that machine and can not use samba. After creating a directory run the following to make sure docker can read and write and those directories
   ```bash
    sudo chown -R <id>:<id> /<path1>
    sudo chown -R <id>:<id> /<path2>
    sudo chown -R <id>:<id> /<path3>
   ```

    Next: [Ngix](../Ngix)
    Layout: [Layout](../Layout)
