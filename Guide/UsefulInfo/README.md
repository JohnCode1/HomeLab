# 🧠 Useful Information

## 🌐 Networking

* ⚠️ **Caution:** This is a critical section. An improper setup can expose you to security risks. Proceed with care.

* When you go through this guide, you will need to know a little about your current network. First, let's talk about the distinction between **WAN IPs** (Public IPs) and **LAN IPs** (Local/Private IPs).

* When connecting to the internet, your ISP (Internet Service Provider) assigns your router a public IP address. This address is how the outside world communicates with your home network. Your public IP can change over time.

* Every time you connect a device (like your computer, phone, or home server) to your internet via Wi-Fi or an Ethernet cable, your router assigns it a private IP address.

  * This happens because your router creates a **Local Area Network (LAN)** that is isolated from the internet. Most default setups use a network in the IP ranges of `192.168.1.1` to `192.168.1.255`. This is often written as `192.168.1.0/24`.

  * In this case, your router acts as the **"gateway"** on IP `192.168.1.1` and assigns each device an IP address via **DHCP** (Dynamic Host Configuration Protocol).

* If you plan on changing your LAN IP, which is often a good security practice, do a quick search online to find what IP ranges are allowed for LAN networks.

* You might want to consider upgrading your router or getting a dedicated **firewall**.

  * I currently use **pfSense** as a firewall, which can be a little tricky but gives you a lot of advanced options.

  * Another popular brand is **Unifi**. They generally offer "gateways" that are a combination of a router and a firewall.

* **I do not recommend opening any ports on your router to the WAN (port forwarding)**. Port forwarding is the process of allowing outside connections to a specific device on your internal network. This can be a security risk as it exposes your home server to the entire internet.

* A much safer way to connect to your home server from outside your home is by using an **overlay VPN**. This creates a secure, private tunnel to your home network, allowing only authorized users to access it. This method greatly reduces your attack surface compared to port forwarding.

* Later in this guide, we will get a domain name via **Cloudflare**, which is not required but makes it easier to access your services by using a human-readable name (e.g., `myserver.com`) instead of an IP address.

  * ⚠️ **Warning:** When purchasing a domain, make sure the TLD (e.g., `.com`, `.net`, `.org`) allows for **WHOIS masking**. This feature hides your personal registration information from the public. The `.us` TLD, for example, does **not** allow this. Always search for "WHOIS privacy" for a domain provider before you buy.

  * You should be able to find a good domain name for about `$7 - $12` per year. Be cautious of providers with expensive renewal fees.

## 🖥️ Proxmox

* **Proxmox** is a powerful, open-source server virtualization management platform. It allows you to create and manage both Virtual Machines (VMs) and containers from a single web interface.

* Once everything is set up, it works very well. However, if you run into problems, it can get complicated fast. Sometimes, it's easier to restart from scratch than to try and fix a small mistake.

* **Proxmox Quirks:** Without a paid subscription, a pop-up will appear when you log in. You can simply press the **Escape** key to close it if the "OK" button doesn't work.

* **Clustering:** This means running multiple PCs together as a single unit to share resources and provide redundancy. This is an advanced topic, and once you cluster machines, it is very difficult to separate them.

## 🐧 Linux

* **Linux** is an open-source operating system that is widely used for servers and home labs. This guide uses it for many of the applications and server management tasks.

* Here are some essential basic commands you will need:

  * `ls`: **L**i**s**ts the files and directories in your current location.

  * `cd [directory]`: **C**hanges **d**irectory. For example, `cd documents` moves you into the "documents" folder.

  * `cd ..`: Moves you **up** one level from your current directory.

  * `cd ~`: Takes you to your user's home directory.

  * `mkdir [name]`: **M**a**k**es a new **dir**ectory (folder).

  * `rm [file]`: **R**e**m**oves (deletes) a file. Be careful—this is permanent!

  * `pwd`: **P**rints the **w**orking **d**irectory (shows you where you are).

  * `sudo`: Stands for **S**uper**u**ser **do**. It allows you to run a command with administrative or root privileges. Use this command with caution.

  * You can run multiple commands at once using `&&`. For example: `command1 && command2` will run `command2` only if `command1` is successful.

## 🗄️ VMs and Containers: What's the Difference?

* **Virtual Machines (VMs)**: Think of a VM as a complete, separate computer running inside your main computer. It has its own operating system (OS), virtual hardware (CPU, RAM, storage), and applications. This offers full isolation but uses more resources.

* **Containers (e.g., Docker)**: Think of a container as a lightweight, isolated application running on your existing OS. It shares the host's OS kernel but has its own file system and libraries. This is much more efficient and uses fewer resources than a VM.

## 🐳 Docker Containers

* **Docker** is a platform that makes it easy to create, deploy, and run applications in containers.

* The way it works, in simple terms, is that developers create **"images"**—these are read-only templates that contain the application and all its dependencies. For example, an image might say, "use the Linux 24.04 OS and download Python."

* You can run a container by specifying an image from **Docker Hub**, which is a public repository of images.

  * ⚠️ **Warning:** Only use trusted and official sources from Docker Hub.

* **Key Commands:**

  * `docker run [image] -d`: Runs the image in a new container. The `-d` flag runs it in the background (**d**etached) so it doesn't take over your terminal.

  * `docker ps -a`: Lists all running and stopped containers (`-a` for **a**ll).

  * `docker stop [container name]`: Stops a running container.

  * `docker --help`: Displays a list of all Docker commands.

* For more complex applications, we will use **Docker Compose**, which is a tool for defining and running multi-container Docker applications.

  * This uses a `compose.yml` file to specify all the images you need, along with their settings and configuration options.

  * `docker compose up -d`: Starts all services defined in the `compose.yml` file.

  * `docker compose down`: Stops and removes the services defined in the `compose.yml` file.

## 🔒 Helpful Privacy Tips

* A key benefit of self-hosting is that you have more control over your data. With services like Google Cloud, you cannot prevent them from accessing your data as they see fit.

* A few ways to enhance your privacy with little effort:

  * **Use a VPN (Virtual Private Network).** This encrypts your internet traffic, hiding your activity from your ISP. Just be sure to choose a reputable VPN provider that has a no-log policy.

  * **Use a privacy-focused browser.** For example, Firefox allows you to set strict privacy modes.

  * **Install privacy-focused extensions.** Examples include **uBlock Origin** (to block ads and trackers) and **Privacy Badger** (to automatically block trackers).

  * **Consider using a service like Kasm.** This is not necessary for most users, but it can be useful if you're ever afraid to click on certain links. It creates a temporary, sandboxed environment that is easily destroyed, so any malicious code cannot affect your main system.

* **Use a Password Manager:** This is a crucial step for securing your homelab and all your online accounts. A password manager helps you create and store unique, strong passwords for every service, so a single breach doesn't compromise all your accounts.

Next: [Layout](../Layout)
