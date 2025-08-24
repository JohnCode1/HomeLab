# 🐳 Installing Docker

---

## 💻 Installation Steps

Follow these steps to install Docker on your system.

1.  **Download the Docker installation script.**
    ```bash
    curl -fsSL [https://get.docker.com](https://get.docker.com) -o get-docker.sh
    ```

2.  **Run the installation script.**
    ```bash
    sudo sh get-docker.sh
    ```

3.  **Verify that Docker is running.**
    ```bash
    sudo systemctl status docker
    ```

4.  **Create the Docker group.**
    This allows non-root users to run Docker commands.
    ```bash
    sudo groupadd docker
    ```

5.  **Add your user to the Docker group.**
    ```bash
    sudo usermod -aG docker $USER
    ```

6.  **Activate the new group changes.**
    You can do this by either logging out and logging back in, or by running the following command.
    ```bash
    newgrp docker
    ```

    Next: [Ngix](../Ngix)
    Layout: [Layout](../Layout)
