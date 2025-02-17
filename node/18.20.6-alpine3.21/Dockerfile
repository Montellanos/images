ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM node:18.20.6-alpine3.21

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create containers based on node"
LABEL version="18.20.6-alpine3.21"
LABEL license="Apache License 2.0"

RUN apk update && apk add --no-cache \
  jq=1.7.1-r0
  