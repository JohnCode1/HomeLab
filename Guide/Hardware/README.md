💻 Hardware Recommendations

    The type of hardware you use is totally up to you.

    If you plan on using apps that might require hardware acceleration (e.g., Jellyfin), consider using an Intel CPU due to their internal graphics.

    To get started and reduce initial costs, use an old computer that you are no longer using.

        💡 I personally use an old laptop with a busted screen for this purpose.

    There are a plethora of mini PCs out there that you can find new or used for a fairly cheap price.

    If you are considering storing a lot of media and have the budget, look into getting a NAS (Network Attached Storage).

        There are some mini NAS options that are cheaper than a normal NAS.

    Before buying any new equipment, especially on a tight budget, keep in mind that you might want to get a setup where you can change out components in the future, as you might not be able to run everything you want at that moment.

            Example: Building your own mini PC.

    If you plan on running local LLMs, look into a setup that supports attaching a GPU.

        This is not required, as I was able to run some small LLMs on my old laptop fairly decently, but note that you will not get the same quality and speed as a setup with a GPU.

⚙️ My Current Setup

    Lenovo Ideapad 1: This is my main workstation I use to connect to my VMs.

    Old busted screen HP laptop: This is currently running Proxmox.

    Custom-built PC: This used to be my main workstation and is now also running Proxmox.

        I swapped most of my apps from my laptop to this machine. When I need a Linux or Windows desktop, I just spin up that VM.

        While this does result in some performance loss compared to running the OS directly, it does not affect me with my current hardware and use case.

✅ Bare Minimum Requirements

    A computer to connect to your Proxmox server.

    A computer to run Proxmox that you can plug an Ethernet cable into.

        The recommended way to use Proxmox is via Ethernet.

    A USB drive to install Proxmox on.

    An Ethernet cable.

    A router with an open Ethernet port.

    ⚠️ Warning: If you are using a laptop, it is recommended to remove the battery, as it could potentially swell from being constantly plugged in.

Next: [[UsefulInfo.md]]
Layout: [[Layout.md]]
