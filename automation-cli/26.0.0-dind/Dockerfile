FROM docker:26.0.0-dind

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="26.0.0-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.50.1
ENV ARGOCD_VERSION=v2.10.6

RUN apk add --no-cache \
  openssl=3.1.4-r5 \
  busybox=1.36.1-r15 \
  openssh-client-common=9.6_p1-r0 \
  openssh=9.6_p1-r0 \
  wget=1.21.4-r0 \
  jq=1.7.1-r0 \
  git=2.43.0-r0 \
  xmlstarlet=1.6.1-r2 \
  aws-cli=2.13.25-r0

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm trivy.tar.gz

RUN wget --no-verbose https://github.com/argoproj/argo-cd/releases/download/${ARGOCD_VERSION}/argocd-linux-amd64 -O /usr/local/bin/argocd \ 
  && chmod +x /usr/local/bin/argocd
