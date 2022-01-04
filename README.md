# Minecraft Server running in a docker container, set up with docker-compose
### Based on https://github.com/itzg/docker-minecraft-server
Personal Minecraft server set up using docker-compose _(tested in an Oracle Cloud VM)_  

#### _WIP_  

- [ ] Testing on the OCI insatnce[^1]
- [X] yml docker-compose file
- [ ] Write the README
- [ ] Just play

[^1]: Testing footnotes

### Table of contents

<!--ts-->
   * [Setup](#setup)
      * [Opening ports](#opening-ports)
   * [Running](#running)
      * [Starting the server](#starting-the-server)
      * [Execute Minecraft commands](#execute-minecraft-commands)

<!--te-->

## Setup

### Opening ports
Open port **25565** tcp **and** udp in the firewall of the VNIC (from 0.0.0.0/0)

## Running

### Starting the server
`cd` to the mc-server-docker folder (where the docker-compose.yml file is situated) and  

```shell
docker-compose up -d
```
  
### Execute Minecraft commands
If rcon is enabled (default):  

```shell
docker exec minecraft-server rcon-cli <COMMAND>
```
  
> If rcon is disabled:  
> 
> ```shell
> docker exec minecraft-server mc-send-to-console <COMMAND>  
> ```
>
