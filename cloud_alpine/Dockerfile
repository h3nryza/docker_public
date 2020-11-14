FROM alpine:latest

LABEL version="1.0" maintainer="https://github.com/h3nryza"

# Arguments
ARG PACKER_VER=1.5.6
ARG TF_VER=0.12.29
ARG GITCLI_VER=1.2.0


# UPDATE
RUN apk update && apk upgrade


# COMMON
RUN apk add bash bash-doc bash-completion curl wget zip  gzip vim openssl util-linux coreutils binutils findutils grep

# ADMINISTRATION
RUN apk add net-tools tree lynx file python3

# DEVELOPER TOOLS
RUN apk add make git htop build-base nodejs npm


# CLOUD
## AWS CLI
RUN apk add aws-cli

# INFRUSTRUCTURE AS CODE
## Packer
RUN  wget https://releases.hashicorp.com/packer/${PACKER_VER}/packer_${PACKER_VER}_linux_amd64.zip && \ 
unzip packer_${PACKER_VER}_linux_amd64.zip && rm -rf packer_${PACKER_VER}_linux_amd64.zip  && \ 
mv packer /usr/local/bin

## TERRAFORM
RUN  wget https://releases.hashicorp.com/terraform/${TF_VER}/terraform_${TF_VER}_linux_amd64.zip && \ 
unzip terraform_${TF_VER}_linux_amd64.zip && rm -rf terraform_${TF_VER}_linux_amd64.zip  && \ 
mv terraform /usr/local/bin/

# CONTAINERS
## KUBERNETES
RUN curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" && \ 
chmod +x ./kubectl && \ 
mv ./kubectl /usr/local/bin/kubectl

## HELM
RUN curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3  && \ 
chmod 700 get_helm.sh && \ 
./get_helm.sh

## EKSUtil
RUN curl --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp && \ 
chmod +x /tmp/eksctl && \ 
mv /tmp/eksctl /usr/local/bin

## SNYK
RUN npm install -g snyk

# Create drive for user data
#ForDriveMount
RUN mkdir /opt/userdata -p


# ALIAS
RUN echo 'alias k=kubectl' >>~/.profile && \
echo 'alias tf=terraform' >>~/.profile && \
echo 'alias eks=eksctl' >>~/.profile


# AUTO COMPLETE
RUN apk add git-bash-completion py3-pip-bash-completion aws-cli-bash-completion

# LAST INSTALLS
RUN sed -i -e 's/v[[:digit:]]\..*\//edge\//g' /etc/apk/repositories && \
sed -i -e 's/v[[:digit:]]\..*\//edge\//g' /etc/apk/repositories && \
apk update && \
apk add yq



