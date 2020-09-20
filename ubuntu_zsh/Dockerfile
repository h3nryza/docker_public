FROM linuxbrew/linuxbrew:latest

LABEL version="1.0" maintainer="https://github.com/h3nryza"
#https://github.com/ohmyzsh/ohmyzsh
#https://medium.com/wearetheledger/oh-my-zsh-made-for-cli-lovers-installation-guide-3131ca5491fb

# Arguments
ARG PACKER_VER=1.5.6
ARG TF_VER=0.12.29

# UPDATE
RUN sudo apt-get update -y

# COMMON
RUN sudo apt install -y bash bash-doc bash-completion curl wget zip  gzip vim openssl apt-utils fonts-powerline nano

# ADMINISTRATION
RUN sudo apt install -y net-tools tree lynx file

# DEVELOPER TOOLS
RUN sudo apt install -y make git htop make nodejs npm zsh git-flow

#Install oh-my-zsh
RUN /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install plugins

## Auto suggestions
RUN git clone https://github.com/zsh-users/zsh-autosuggestions
RUN sudo mkdir /.oh-my-zsh/custom/plugins/ -p
RUN sudo mv zsh-autosuggestions /.oh-my-zsh/custom/plugins/zsh-autosuggestions

## Highliting
RUN git clone https://github.com/zsh-users/zsh-syntax-highlighting
RUN sudo mv zsh-syntax-highlighting /.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
RUN sed -i 's/plugins=(git)/plugins=(git,autosuggestions,syntax-highlighting)/' ~/.zshrc

#af-magic.zsh-theme

#ForDriveMount
RUN sudo mkdir /opt/userdata -p





