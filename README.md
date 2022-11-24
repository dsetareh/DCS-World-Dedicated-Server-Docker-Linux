# DCS World Dedicated Server Linux

[Useful reddit thread, used to build this guide](https://old.reddit.com/r/hoggit/comments/ns6g7j/you_can_run_dedicated_server_on_linux_here_is_how/)

Runs on a virtual desktop docker container accessed via webui/vnc (or ssh/xrdp if you wanna set that up)
~150GB of space required for the container and the game files



## 1. Clone repo
    
```bash
git clone
cd dcs-dedicated-server
```

## 2. Edit the docker-compose.yml

```yaml
environment:
    - USER=dcsuser # if you change this you will need to change the volume mount
    - PASSWORD=yourpassword # change this
    - VNC_PASSWORD=yourpassword # change this
```

## 3. Build and Run the container
#### *this will take a while*

```bash
docker-compose up -d --build
```

## 4. Gain access to remote desktop

```yaml
      - 16612:80 # access port 16612 on the host for webvnc (password in docker-compose)
      # ...
      - 16613:5900 # or use an actual vnc client (password in docker-compose)
```



## 5. Install DCS World Dedicated Server
### Open Lutris
<img src="img/1.png" width="300"/>

### Add Game, then Search Lutris Website for Installers
<img src="img/2.png" width="300"/>

### Search for DCS World Open Beta Dedicated Server
#### *(You can choose to run the stable version in the next step)*
<img src="img/3.png" width="300"/>

### Select desired version of DCS World Dedicated Server
<img src="img/4.png" width="300"/>

### Install, following directions
#### *this will take a while*
<img src="img/5.png" width="300"/>

#### *defaults*
<img src="img/6.png" width="300"/>


## 6. Download/Update DCS Game Data
#### The server will prompt you to download about 60Gb of game data. Similarly to the game, these files will need to be periodically updated.
<img src="img/7.png" width="300"/>

#### *this will take a while*
<img src="img/8.png" width="300"/>


## 6. Launch DCS World Dedicated Server
<img src="img/9.png" width="300"/>


## 7. Log In
<img src="img/11.png" width="300"/>

#### If you get a black window and no login prompt, use this command (in a terminal on the container) to move the login window to a visible portion of the screen
```bash
xdotool windowmove $(xdotool search --onlyvisible 'DCS Login') 10 10
```
<img src="img/10.png" width="300"/>


#### Once you see this window (the black screen is normal, and will persist), the server is running.
<img src="img/12.png" width="300"/>


## 8. Access Server Control Webui

The DCS Server control WebUI tries to connect to the server on localhost, so it must be either accessed within the container or you must forward the control port to the machine opening the webui. 


#### Navigate to ```/home/dcsuser/Games/dcs-world-open-beta-dedicated-server/dosdevices/c:/Program Files/Eagle Dynamics/DCS World OpenBeta Server/WebGUI``` within the container, and open index.html to access the DCS Server WebUI.
<img src="img/13.png" width="300"/>