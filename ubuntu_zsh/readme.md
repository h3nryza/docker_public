# linuxbrew Docker File for h3nryza

## Container Toolsets

__COMMON__
- bash 
- bash-doc 
- bash-completion 
- curl 
- wget 
- zip  
- gzip 
- vim 
- openssl

__ADMIN__
- net-tools 
- tree 
- lynx 
- file

__DEVELOPMENT__
- make 
- git 
- htop 
- build-base 
- nodejs 
- npm


________________________________________

## Building the container

### Arguements
Used to control the packer and terraform versions

PACKER_VER=1.5.6
TF_VER=0.12.29

### Without build arguments
docker build . --label h3neryza_ubuntu_zsh -t h3nryza/ubuntu_zsh 

### With Arguments
docker build . --build-arg PACKER_VER=1.5.6 --build-arg TF_VER=0.12.29  --label h3nryza_ubuntu_zsh  -t h3nryza/ubuntu_zsh  

________________________________________

## Running the container

### Pulling the contianer
docker pull h3nryza/ubuntu_zsh:latest

### Running the container
docker run -itd --name h3nryza_ubuntu_zsh  -t h3nryza/ubuntu_zsh:latest 

## Running the container with local mountpoint
docker run -itd -v c:/repo:opt/userdata --name h3nryza_ubuntu_zsh h3nryza/ubuntu_zsh:latest  

________________________________________

## Update to docker hub

### Login to docker
docker login

### Docker tag
docker tag {IMAGE_ID} h3nryza/ubuntu_zsh:latest

### Push to docker
docker push h3nryza/ubuntu_zsh:latest

### Logout of docker
docker logout

________________________________________

# Handy Information

## Links
Docker Hub Lin
https://hub.docker.com/

Docker Hub Profile Link
https://hub.docker.com/repository/docker/h3nryza 

CMD vs Entrypoint vs Run
https://goinbigdata.com/docker-run-vs-cmd-vs-entrypoint/#:~:text=RUN%20executes%20command(s)%20in,will%20run%20as%20an%20executable.

________________________________________

## Cleaning containers (PowerShell / Linux)

### Stop all containers
docker stop $(docker ps -qa)

### Remove all images
docker rmi -f $(docker image ls -qa)

### Remove any dangeling items
docker system prune -af

________________________________________
Maintainer:  https://github.com/h3nryza


