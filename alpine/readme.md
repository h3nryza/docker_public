# Alpine Docker File for h3nryza

## Building the container

### ARGUMENTS
Used to control the packer and terraform versions

PACKER_VER=1.5.6
TF_VER=0.12.29

### Without build arguments
docker build . --label h3nryza_alpine -t henryza:alpine 

### With Arguments
docker build . --build-arg PACKER_VER=1.5.6 --build-arg TF_VER=0.12.29  --label h3nryza_alpine -t h3nryza:alpine 

## Running the container

### Pulling the contianer
docker pull 3nryza/h3nryza_alpine:latest

### Running the container
docker run -itd --name alpine_h3nryza h3nryza/h3nryza_alpine:latest 

## Running the container with local mountpoint
docker run -itd -v /c:/repo/opt/userdata --name alpine_h3nryza h3nryza/h3nryza_alpine:latest  


## Update to docker hub

### Login to docker
docker login

### Docker tag
docker tag {IMAGE_ID} h3nryza/h3nryza_alpine:latest

### Push to docker
docker push h3nryza/h3nryza_alpine:latest

### Logout of docker
docker logout

# Handy Information

## Links
Docker Hub Lin
https://hub.docker.com/

Docker Hub Profile Link
https://hub.docker.com/repository/docker/h3nryza 

CMD vs Entrypoint vs Run
https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/#:~:text=RUN%20executes%20command(s)%20in,will%20run%20as%20an%20executable.

## Cleaning containers

### Stop all containers
docker stop $(docker ps -q)

### Remove all images
docker rmi -f $(docker image ls -q)

### Remove any dangeling items
docker system prune -af