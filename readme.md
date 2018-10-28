# FTB Sky Adventures Server Docker Image

I have no affiliation with this modpack or the creators, 
and am only doing this for the enjoyment of other people who enjoy this modpack.

## Docker
https://hub.docker.com/r/palexcast/ftb-sky-adventures/

## Running the docker image
```
docker run -itd \
-p 25565:25565 -p 25565:25565/udp \
-v /home/skyblock/saves/world:/minecraft/world \
--name ftb palexcast/ftb-sky-adventures
```

## Override settings.sh
`-Dfml.queryResult=confirm"` may be required for the server to start correctly.

If you wish to override settings, for example memory allocation, create a settings-local.sh file, 
and add the parameter under to the docker run command.
```
-v /{my-folder-path}/settings-local.sh:/minecraft/settings-local.sh
```

Example:
```
docker run -itd \
-p 25565:25565 -p 25565:25565/udp \
-v /home/skyblock/saves/world:/minecraft/world \
-v /{my-folder-path}/settings-local.sh:/minecraft/settings-local.sh \
--name ftb palexcast/ftb-sky-adventures
```


## Useful commands
### Print most recent console lines
`docker logs ftb`

### Attach to the docker container, can be used to write commands on the minecraft server.
If doing this, remember to not close the console with `ctrl` + `c` as this will stop the server.
`docker attach ftb`


### Open a new console window inside the docker container
`docker exec sh ftb`