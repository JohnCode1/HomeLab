# Setting up back up
- - -
Right now I am I am just manual backing up each VM due to limited resources
1. go to click backup -> backupnow and i just do a snap shot.

Using another proxmox vm:
1. install proxmox back up server onto your iso images
2. create vm select iso image of back up server
3. add your disk for your os and storage
4. select your cores and ram
5. start up and set up for my host name use something lick backup.local or backup.arpa
6. got your ip set up and login
7. go to proxmox omunity scripts and use proxmox backup server post install
8. select yes to all except pbtest repo
9. go to storage disk
10. create a zfs pool
11. compression lz4
12. go to dashboard and copy your fingerprint
13. go to datacenter storage add proxmox back up server
14. enter credentials
15. go to backup add select node to bac storage is the proxmox server choose schedule and selection mode
16. choose your retention
17. mode snapshot
18. create
19. go to your vms and containers select back up and make sure back up is checked
20. test by running it now
Next: [Docker](../Docker)
Layout: [Layout](../Layout)
