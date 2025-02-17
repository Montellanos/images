ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM ubuntu:20.04

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Ubuntu based image to compile ionic web based proyects"
LABEL version="5.0.3-ubuntu20.04"
LABEL license="Apache License 2.0"

RUN apt-get update && \
    apt-get install -y \
    software-properties-common=0.99.9.12

RUN add-apt-repository ppa:git-core/ppa

RUN apt-get update && \
    apt-get install -y \
    git=1:2.48.1-0ppa1~ubuntu20.04.1 \
    curl=7.68.0-1ubuntu2.25

RUN apt-get clean

RUN rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://deb.nodesource.com/setup_14.x | grep -v 'sleep' | bash -

RUN apt-get install -y nodejs=14.21.3-deb-1nodesource1

RUN npm install -g ionic@5.0.3
RUN npm install -g cordova@11.0.0
