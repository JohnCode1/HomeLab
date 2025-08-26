WARNING I DO NOT CONDONE PIRACY OR ILLEGAL DOWNLOADS
# Setup
* This docker file will contain:
  * glueten, qbittorrent, duenhealth, nzbget, prowlarr, sonarr, radarr, lidarr, bazarr
* this must also have its docker file locally on this server
1. create or navigate to your dirrectory to store your docker file
```bash
sudo mkdir torrentusenet
cd torrentusenet
```
2. Give your user permisions read and write in that directory
3. pull my docker and .env file for the torrentusenet stack
4. change all the <> in the stack
5. run docker compose up -d
6. check logs of all docker containers
7. test glueten conectivity docker run --rm --network=container:gluetun alpine:3.18 sh -c "apk add wget && wget -qO- https://ipinfo.io"
    docker exec -it container_name bash
wget -qO- https://ipinfo.io
8. go to qbit torrent via :8080 and login and get password from the docker logs
9. change password setting -> webui ->change password -> save
10. restart docker qbittorrent and relogin
11. go to connections and verify correct port
12. go to advanced network interface -> tun 0 -> save
13. go to downloads and change directories to perfered set up for default save path, incolmplete, and .torrent files
14. test by copying ubuntu 24.04 torrent link
15. login to qbit on port 6789 with default username of nzbget and password of tegbzn6789
16. go to security and change username and password -> save and relogin
17. go to settings incoming nzbs and turn off appendcategorydir -> save
18. go to settings -> paths and chaing main dest, and inter dir to your perfered path ->save
19. login into prowlerr 9696 authentaction medthos login pathabd enter username and password -> save
20. add your perfered indexers
21. go to settings download client ->nzbget change host to your ip on glueten
22. enter nzbget user name and password choose default category -> save
* sonarr,lidar, bazarr, and radarr are same set ups and would recommend doing this for each app at the same time
24. login to apps enter ip and port choose forms and create username and login
25. go to settings -> general -> api key and copy
26. in prowler go to settings and app your setting up and enter in api key and ip of that host
27. for bazar after set up to radarr go to settings languages and enter the language filter save and add profile -> add language -> save -> save then go to providers and select your provider of choice
27. after setting up apps go to movies in radarr and import existing movies from your data directory
28.go to settings and add your download clients
29. test by searching for a movie that you can obtain legally and download it

Next: [Jellyfin](../Jellyfin)
Layout: [Layout](../Layout)
