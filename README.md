# Minecraft Server running in a docker container, set up with docker-compose
### Based on https://github.com/itzg/docker-minecraft-server
Personal Minecraft server set up using docker-compose _(tested in an Oracle Cloud VM)_  

#### _WIP_  

- [X] Testing on the OCI instance
- [X] yml docker-compose file
- [ ] Write the README[^1]
- [X] Just play

[^1]: Everything is already explained in https://github.com/itzg/docker-minecraft-server

### Table of contents

<!--ts-->
   * [Setup](#setup)
      * [Opening ports](#opening-ports)
   * [Running](#running)
      * [Starting the server](#starting-the-server)
      * [Execute Minecraft commands](#execute-minecraft-commands)
      * [Stopping the server](#stopping-the-server)

<!--te-->

## Setup
You should have [**Docker**](https://docs.docker.com/) (with `docker-compose`, or not if you use the newer `docker compose`) installed on your server.  

Copy the [`docker-compose.yml`](docker-compose.yml) file (or git clone this repo) in a folder (i.e _mc-server-docker_ folder: `mkdir mc-server-docker`).

### Opening ports
Open port **25565** tcp **and** udp in the firewall of the subnet of the instance's VNIC, (from 0.0.0.0/0).

## Running

### Starting the server
Make sure you are in the folder where the .yml is located (`cd` to the mc-server-docker directory) and : 

```shell
sudo docker-compose up -d
```
(`-d` makes sure the container is running in "detached" mode, meaning you can still interact with your linux machine when the coantiner is running, it basically makes the container run in the background)

**The server is now running!**  

You can check the logs using `sudo docker logs -f minecraft-server`,  
where `minecraft-server` is the name of the container (`container_name` in the docker-compose.yml).  
(`-f` is for "following" the logs, you can exit by pressing _CTRL+C_)

The minecraft server's files can be found in the `minecraft-server` folder within the `mc-server-docker` directory, if you want to download or barckup them up, or edit the server.properties directly (only after running the docker container for the first time, as they are generated).
  
### Execute Minecraft commands
If rcon is enabled (default):  

```shell
sudo docker exec minecraft-server rcon-cli <COMMAND>
```
  
> If rcon is disabled:  
> 
> ```shell
> sudo docker exec minecraft-server mc-send-to-console <COMMAND>  
> ```
>

where `<COMMAND>` is the minecraft command executed by the server. 

### Stopping the server
To stop the server simply execute, in the directory where the `docker-compose.yml` is located, 
```shell
sudo docker stop minecraft-server
```

And to start it again simply do:
```shell
sudo docker start minecraft-server
```

### Restarting the server
```shell
sudo docker restart minecraft-server
```
