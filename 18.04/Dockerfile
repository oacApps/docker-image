#Download base image ubuntu 18.04
FROM ubuntu:18.04
# Update Ubuntu Software repository
RUN apt update  && apt install -y sudo
RUN apt-get update && apt-get install -y iputils-ping
RUN adduser --disabled-password --gecos '' docker
RUN adduser docker sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER docker

########## Install Docker ##########

# Update the apt package index and install packages to allow apt to use a repository over HTTPS
RUN sudo apt install \
    apt-transport-https -y \
    ca-certificates  -y \
    curl  -y \
    gnupg-agent  -y \
    software-properties-common  -y

# Add Docker’s official GPG key:

RUN sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

RUN sudo add-apt-repository -y \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

# INSTALL DOCKER ENGINE
RUN sudo apt-get install docker-ce docker-ce-cli containerd.io -y

USER docker
CMD /bin/bash
