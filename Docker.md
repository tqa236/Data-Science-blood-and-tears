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

* [Container Structure Tests](https://github.com/GoogleContainerTools/container-structure-test)

Must put `schemaVersion:       "2.0.0"` in the beginning of a test file.

* [Set up Docker with GPU](http://collabnix.com/introducing-new-docker-cli-api-support-for-nvidia-gpus-under-docker-engine-19-03-0-beta-release/)

* [Connect to jupyter notebook running in docker in a remote server](https://stackoverflow.com/questions/54572456/connect-to-jupyter-notebook-running-in-docker-on-a-remote-server)

In the remote machine:

```
docker run -it -p 8080:8888 -p 6006:6006 -v ~/:/host waleedka/modern-deep-learning
```

In the local machine:

```
ssh -N -L localhost:8000:localhost:8080 username@remoteHostIp
```

* Use `--rm` flag for short commands and `-d` flag for long commands that we want to run in the background

* Run a script inside a Docker container with `bash my_script.sh`, not `./my_script.sh`

* [Run Python faster with Docker](https://medium.com/better-programming/faster-python-in-docker-d1a71a9b9917)

Add `--security-opt seccomp=unconfined` flag when creating the container. Only for trusted code of course. Or in desperated situation.

First port: external port.

* [Build again one service with `docker-compose`](https://stackoverflow.com/questions/35228970/docker-compose-build-single-container)

```console
docker-compose up -d --no-deps --build <service_name>
```

* [Check the health of Docker containers with docker-bench](https://github.com/docker/docker-bench-security)

* [Run Python code faster in Docker](https://medium.com/better-programming/faster-python-in-docker-d1a71a9b9917)

(Security concern)

```
docker run -it --security-opt seccomp=unconfined 4oh4/pi
```
