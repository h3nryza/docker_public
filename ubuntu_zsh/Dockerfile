FROM linuxbrew/linuxbrew:latest

LABEL version="1.0" maintainer="https://github.com/h3nryza"

# Arguments
ARG PACKER_VER=1.5.6
ARG TF_VER=0.12.29

# UPDATE
RUN sudo apt-get update -y

# COMMON
RUN sudo apt install -y bash bash-doc bash-completion curl wget zip  gzip vim openssl

# ADMINISTRATION
RUN sudo apt install -y net-tools tree lynx file

# DEVELOPER TOOLS
RUN sudo apt install -y make git htop make nodejs npm

#Install Brew
#RUN /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

#Install oh-my-zsh
RUN sudo apt-add-repository ppa:git-core/ppa
RUN sudo apt-get update
RUN sudo apt-get install zsh -y
RUN curl -L https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh | bash
RUN /bin/bash -c echo "skip_global_compinit=1" >>/etc/zsh/zshenv
RUN /bin/bash -c echo "ZSH_DISABLE_COMPFIX="true" >>/etc/zsh/zshenv
RUN sudo bash -c zsh


#ForDriveMount
RUN mkdir /opt/userdata -p

