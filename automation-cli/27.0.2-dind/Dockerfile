ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM docker:27.0.2-dind-alpine3.20

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="27.0.2-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.59.0
ENV ARGOCD_VERSION=2.13.4

RUN apk update && apk add --no-cache \
  openssl=3.3.2-r1 \
  busybox=1.36.1-r29 \
  openssh-client-common=9.7_p1-r4 \
  openssh=9.7_p1-r4 \
  wget=1.24.5-r0 \
  jq=1.7.1-r0 \
  git=2.45.3-r0 \
  xmlstarlet=1.6.1-r2 \
  speedtest-cli=2.1.3-r7 \
  aws-cli=2.15.57-r0 \
  curl=8.11.1-r0 \
  libexpat=2.6.4-r0 \
  libcurl=8.11.1-r0 \
  tzdata=2024b-r0 \
  coreutils=9.5-r2

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm -rf trivy.tar.gz

RUN wget --no-verbose https://github.com/argoproj/argo-cd/releases/download/v${ARGOCD_VERSION}/argocd-linux-amd64 -O /usr/local/bin/argocd \ 
  && chmod +x /usr/local/bin/argocd
