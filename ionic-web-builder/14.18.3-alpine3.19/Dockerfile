FROM node:14.18.3-alpine3.15

COPY . .

RUN export COUNTRY_CODE=PA

RUN sh create-environment.sh

RUN npm install --force


# FROM alpine:3.19.1

# LABEL maintainer="Jorge Montellanos Díaz"
# LABEL description="Alpine based image to compile ionic web based proyects"
# LABEL version="14.18.3-alpine3.19"
# LABEL license="Apache License 2.0"

# ENV NODE_VERSION=14.18.3
# ENV PYTHON_VERSION=3.10.14


# RUN apk update && apk add --no-cache \
#   wget=1.21.4-r0 \
#   build-base=0.5-r3 \
#   libffi-dev=3.4.4-r3 \
#   openssl-dev=3.1.4-r6 \
#   zlib-dev=1.3.1-r0 \
#   bzip2-dev=1.0.8-r6 \
#   pcre-dev=8.45-r3

# RUN wget --no-verbose https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tar.xz \
#   && tar -xf Python-${PYTHON_VERSION}.tar.xz \
#   && cd Python-${PYTHON_VERSION} \
#   && ./configure --enable-optimizations --with-ensurepip=install \
#   && make install -s \
#   && cd .. \
#   && rm -rf Python-${PYTHON_VERSION}.tar.xz \
#   && rm -rf Python-${PYTHON_VERSION} 


# RUN wget https://nodejs.org/dist/v14.18.3/node-v14.18.3.tar.xz

# RUN tar -xf node-v14.18.3.tar.xz

# WORKDIR /node-v14.18.3

# RUN ./configure
# RUN make install -s

# RUN node -v
# # RUN npm -v


