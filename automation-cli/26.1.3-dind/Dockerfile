ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM docker:26.1.3-dind-alpine3.19

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="26.1.3-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.60.0
ENV ARGOCD_VERSION=2.14.4

RUN apk update && apk add --no-cache \
  openssl=3.1.8-r0 \
  busybox=1.36.1-r19 \
  openssh-client-common=9.6_p1-r2 \
  openssh=9.6_p1-r2 \
  wget=1.21.4-r0 \
  jq=1.7.1-r0 \
  git=2.43.6-r0 \
  xmlstarlet=1.6.1-r2 \
  speedtest-cli=2.1.3-r6 \
  aws-cli=2.15.14-r0 \
  curl=8.12.1-r0 \
  libexpat=2.6.4-r0 \
  tzdata=2025a-r0 \
  coreutils=9.4-r2 \
  musl=1.2.4_git20230717-r5 \
  musl-utils=1.2.4_git20230717-r5 

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm -rf trivy.tar.gz

RUN wget --no-verbose https://github.com/argoproj/argo-cd/releases/download/v${ARGOCD_VERSION}/argocd-linux-amd64 -O /usr/local/bin/argocd \ 
  && chmod +x /usr/local/bin/argocd
