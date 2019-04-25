# Docker - Today I learn

* Fix Docker error: request canceled while waiting for connection 

(Source: https://github.com/docker/kitematic/issues/2956)

Go to Docker settings > network > DNS server . change from automaic to fixed ( default is 8.8.8.8 )

* Cannot open localhost

```
docker run -it -p 8888:8888 image:version
```

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
