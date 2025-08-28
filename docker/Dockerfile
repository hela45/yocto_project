
#Define Ubunutu
FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
#Install Yocto dependencies 

RUN  apt-get -y update && apt install -y build-essential chrpath cpio debianutils \
diffstat file gawk gcc git iputils-ping libacl1 liblz4-tool locales python3 \
python3-git python3-jinja2 python3-pexpect python3-pip python3-subunit socat\
 texinfo unzip wget xz-utils zstd python3.10-venv


RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen && locale-gen
ENV LANG=en_US.UTF-8

#Install KAS 

ENV VIRTUAL_ENV=/gate-venv
RUN python3 -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

RUN pip3 install kas

#Create a new user and group 
RUN useradd -m -s /bin/bash -u 1000 -G sudo hela \
    && echo "hela ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

#Create a volume to share the project directory: for me i will do a mount :docker run -it -v $HOME/project:/yocto-qemu-proj1 yocto-build

#Switch to the new user and setup the working directory


USER hela
WORKDIR /home/hela



