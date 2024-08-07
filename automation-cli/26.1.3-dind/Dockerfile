ARG PLATFORM=linux/amd64
FROM --platform=$PLATFORM docker:26.1.3-dind-alpine3.19

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="26.1.3-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.54.1
ENV ARGOCD_VERSION=2.12.0

RUN apk update && apk add --no-cache \
  openssl=3.1.6-r2 \
  busybox=1.36.1-r19 \
  openssh-client-common=9.6_p1-r1 \
  openssh=9.6_p1-r1 \
  wget=1.21.4-r0 \
  jq=1.7.1-r0 \
  git=2.43.4-r0 \
  xmlstarlet=1.6.1-r2 \
  speedtest-cli=2.1.3-r6 \
  aws-cli=2.15.14-r0 \
  curl=8.9.0-r0 

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm -rf trivy.tar.gz

RUN wget --no-verbose https://github.com/argoproj/argo-cd/releases/download/v${ARGOCD_VERSION}/argocd-linux-amd64 -O /usr/local/bin/argocd \ 
  && chmod +x /usr/local/bin/argocd
