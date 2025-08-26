# Setup: this docker compose file has jellyfin and jellyseer
---
1. Go into or make the directory you will be storing your dockerfile for jellyfin 
*Note: For Jellyfin you need to have that docker file locally on your machine or you might run into issues
    ```bash
    mkdir jellyfindocker
    cd jellyfindocker
    
2. Pull the dockerfile for jellyfin from my repository
   ```bash
   wget https://raw.githubusercontent.com/JohnCode1/HomeLab/main/docker/jellyfin/compose.yml
   ```
   
3. Change 'JellySeers Config file path' 'Jellyfins config and data file path'
   ```bash
   nano compose.yml
   #If not using intel quick sync remove devices as well
   
4. `Cntrl^o` to save and `cntrl^x` to exit
  
5. Run to start up the container
   ```bash
   docker compose up -d
   ```
   
6. after the container is running run to check the logs of the container
   ```bash
   docker logs jellyfin
   docker logs jellyseer
   ```
   
7. Navigate to your browser of choice and enter `<youripofvm/container>:8096`
   
8. Intial Setup: Select Language -> next ->username and password -> next -> add media library -> choose media type -> add folder -> <path to storing data> -> ok -> next -> choose language and region -> next -> check enable auto port mapping -> next -> Finish -> login
   
9. Check jellyfin has proper permisions by deleting some data you have WARNING make sure you have a back up of that data

10. Enable Hardware transcoding: Three bars on left of screen -> Dashboard -> Playback -> Transcoding -> Hardware acceleration select the one you are using -> paste in text of QSV device below the text box -> save

11. Check to make sure transcoding is working for intel: start some data
    ```bash
    sudo intel_gpu_top
    #Enter Password
    ```
12. go to jellyseer via ip and port 5055
13. log in and sync libraries -> scan and add radar and sonarr with ip addresses and ports and api keys -> quality profiles and root folder for data and change minimum availability -> released

Next: [Metube](../Metube)
Layout: [Layout](../Layout)
