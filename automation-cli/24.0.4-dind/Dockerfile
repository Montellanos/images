ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM docker:24.0.4-dind-alpine3.18

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="24.0.4-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.60.0
ENV ARGOCD_VERSION=2.14.4

RUN apk update && apk add --no-cache \
  libcrypto3=3.1.8-r0 \
  libssl3=3.1.8-r0 \
  ssl_client=1.36.1-r7 \
  openssl=3.1.8-r0 \
  busybox=1.36.1-r7 \
  krb5-libs=1.20.2-r1 \
  openssh-client-common=9.3_p2-r3 \
  openssh=9.3_p2-r3 \
  wget=1.21.4-r0 \
  jq=1.6-r4 \
  git=2.40.4-r0 \
  xmlstarlet=1.6.1-r2 \
  speedtest-cli=2.1.3-r5 \
  aws-cli=2.15.14-r0 \
  curl=8.12.1-r0 \
  tzdata=2025a-r0 \
  coreutils=9.3-r2 \
  musl=1.2.4-r3 \
  musl-utils=1.2.4-r3

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm -rf trivy.tar.gz

RUN wget --no-verbose https://github.com/argoproj/argo-cd/releases/download/v${ARGOCD_VERSION}/argocd-linux-amd64 -O /usr/local/bin/argocd \ 
  && chmod +x /usr/local/bin/argocd
