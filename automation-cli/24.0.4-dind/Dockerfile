FROM docker:24.0.4-dind

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="24.0.4-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.47.0

RUN apk add --no-cache \
  python3=3.11.8-r0 \
  py3-pip=23.1.2-r0 \
  wget=1.21.4-r0 \
  jq=1.6-r4 \
  openssl=3.1.1-r3 \
  busybox=1.36.1-r1

RUN pip3 install awscli==1.32.34

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm trivy.tar.gz


