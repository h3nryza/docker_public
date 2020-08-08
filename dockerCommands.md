## BEst practises
https://docs.docker.com/develop/develop-images/dockerfile_best-practices/


## Build commands
docker build -t image:version .
docker build -t image:version -f Dockerfile

## Push
docker login
docker tag image:version repo/image:version
docker push

## Run commands
__interactive__ 	docker run -it --name runName containerName
__daemon__ 			docker run -d  --name runName containerName
__attache__			docker attach runName

## Cleanups

__stop__			docker stop $(docker ps -q))
__prune__			docker container rm -f $(docker ps -aq)
__System-prune__	docker system prune -af
__Image-prune__		docker rmi -f $(docker image ls -q)
__Volume-Prune__	docker volume prune -af
__Aditional_purge__	docker rmi $(docker images -a -q)
docker images purge



## Copy from host to container & container to host
docker copy container:source localDestination
docker copy localSource container:destination

## Logs
```
# See all logs
docker logs ContainerName/ContainerID
# Follow Logs
docker logs --follow ContainerName/ContainerID
# Tail logs
docker logs --tail 2500 ContainerName/ContainerID
# Specific timestamp
docker logs --since 2017-05-03 ContainerName/ContainerID
docker logs --since 2017-05-03T10:00 ContainerName/ContainerID
```

