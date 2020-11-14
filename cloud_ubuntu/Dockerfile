FROM ubuntu:latest

LABEL version="1.0" maintainer="https://github.com/h3nryza"

# Arguments
ARG PACKER_VER=1.5.6
ARG TF_VER=0.12.29
ARG GITCLI_VER=1.2.0
ARG DEBIAN_FRONTEND=noninteractive

# UPDATE
RUN apt update -y && apt upgrade -y

# COMMON
RUN apt install -y bash bash-doc bash-completion  curl wget zip  gzip vim openssl software-properties-common

# ADMINISTRATION
RUN apt install -y net-tools tree lynx file python3.8 python3-pip python3-dev 

# DEVELOPER TOOLS
RUN apt install -y make git htop make nodejs npm

## Github CLI
RUN wget "https://github.com/cli/cli/releases/download/v${GITCLI_VER}/gh_${GITCLI_VER}_linux_amd64.deb"
RUN apt install ./gh_${GITCLI_VER}_linux_amd64.deb


# CLOUD
## AWS CLI
RUN apt install -y awscli 

# INFRUSTRUCTURE AS CODE
## Packer
RUN  wget https://releases.hashicorp.com/packer/${PACKER_VER}/packer_${PACKER_VER}_linux_amd64.zip && \
unzip packer_${PACKER_VER}_linux_amd64.zip && rm -rf packer_${PACKER_VER}_linux_amd64.zip && \
mv packer /usr/local/bin

## TERRAFORM
RUN  wget https://releases.hashicorp.com/terraform/${TF_VER}/terraform_${TF_VER}_linux_amd64.zip && \
unzip terraform_${TF_VER}_linux_amd64.zip && \
rm -rf terraform_${TF_VER}_linux_amd64.zip && \
mv terraform /usr/local/bin/

# CONTAINERS
## KUBERNETES
RUN curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" && \
chmod +x ./kubectl && \
mv ./kubectl /usr/local/bin/kubectl

## HELM
RUN curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 && \
chmod 700 get_helm.sh && \
./get_helm.sh

## EKSUttil
RUN curl --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp && \
chmod +x /tmp/eksctl && \
mv /tmp/eksctl /usr/local/bin

## SNYK
RUN npm install -g snyk

# Create drive for user data
#ForDriveMount
RUN mkdir /opt/userdata -p

# ALIAS
RUN echo 'alias k=kubectl' >>~/.bashrc && \
echo 'alias tf=terraform' >>~/.bashrc && \
echo 'alias eks=eksctl' >>~/.bashrc


# AUTO COMPLETE

## Enable Autocomplete in bashrc
RUN echo " \n\
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then \n\
    . /etc/bash_completion \n\
fi" >> ~/.bashrc

## Kubernetes
RUN echo 'source <(kubectl completion bash)' >> ~/.bashrc && \
echo 'complete -F __start_kubectl k' >> ~/.bashrc

## Terraform
RUN echo "complete -C terraform terraform" >>~/.bashrc && \
echo "complete -C terraform tf" >> ~/.bashrc

## Helm
RUN echo 'source <(helm completion bash)' >> ~/.bashrc && \
echo 'complete -F __start_helm h' >> ~/.bashrc

## AWS
RUN echo "complete -C '/usr/bin/aws_completer' aws" >> ~/.bashrc

## EKSCTL
RUN echo 'source <(eksctl completion bash)' >> ~/.bashrc && \
echo 'complete -F __start_eksctl eks' >> ~/.bashrc

