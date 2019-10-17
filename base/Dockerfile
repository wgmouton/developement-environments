FROM buildpack-deps:bionic

ENV TERM xterm

# Update package manager and add dependencies
RUN apt update

# Install all tools
RUN apt install -y \
  apt-transport-https \ 
  gnupg \
  libssl1.0-dev \
  locales \
  zsh \
  powerline \
  fonts-powerline \
  nano \
  vim \
  git \
  curl \
  wget 

WORKDIR /root

ADD ./configs/.zshrc .zshrc
ADD ./configs/.vimrc .vimrc

# Setup locale settings
RUN locale-gen en_US.UTF-8

# Install Node Js
RUN \
  curl -sL https://deb.nodesource.com/setup_10.x | -E bash - &&\
  apt update &&\
  apt install -y nodejs nodejs-dev node-gyp npm yarn 

# Install kubectl & Helm
RUN \
  curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - &&\
  echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list &&\
  apt update &&\
  apt install -y kubectl &&\
  curl -L https://git.io/get_helm.sh | bash


# Instal oh-my-zsh
RUN \
  git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh --depth 1 &&\
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.zsh-syntax-highlighting --depth 1 &&\
  chsh -s /bin/zsh

# Configure VIM
# git clone https://github.com/gmarik/Vundle.vim ~/.vim/bundle/Vundle.vim &&\

# RUN \
#   curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim &&\
#   vim +PluginInstall

WORKDIR /root/workspace

ENTRYPOINT [ "zsh" ]