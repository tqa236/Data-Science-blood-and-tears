# Docker - Today I learn

* Fix Docker error: request canceled while waiting for connection 

(Source: https://github.com/docker/kitematic/issues/2956)

Go to Docker settings > network > DNS server . change from automaic to fixed ( default is 8.8.8.8 )

* Cannot open localhost

```
docker run -it -p 8888:8888 image:version
```

First port: external port.
Second port: internal port.

* Kill all running containers

```
docker kill $(docker ps -q)
```

* Delete all stopped containers

```
docker rm $(docker ps -a -q)
```

* Delete all images

```
docker rmi $(docker images -q)
```

* Mount a host directory to a container (Windows)

```
docker run -v d:/data:/data alpine ls /data
```

* Access to a container's terminal

```
docker exec -it container_name /bin/bash
docker exec -it -u root container_name /bin/bash

```

* Install ping in Docker

```
apt update
apt install iputils-ping
```

* Check Ubuntu version inside a Docker container

```
cat /etc/lsb-release
```

* Fix `Error response from daemon: driver failed programming external connectivity on endpoint` error on Windows 10: restart Docker

* [Delete all containers of a specific image](https://stackoverflow.com/questions/32073971/stopping-docker-containers-by-image-name-ubuntu)

```
docker rm $(docker stop $(docker ps -a -q --filter ancestor=<image-name>))
```

* [Mounted volume is empty inside container after changing Windows password](https://stackoverflow.com/questions/38583900/mounted-volume-is-empty-inside-container)

We need to disable drive sharing (and click "Apply") and re-enable it again (and click "Apply").

* Sometimes (when?), it's necessary to [increase the resources allocating to Docker](https://stackoverflow.com/questions/44907444/error-137-on-docker-build-command-on-win7)

* Use bind mount for local development and COPY in production
(https://hackernoon.com/how-to-move-code-into-a-docker-container-ab28edcc2901)
