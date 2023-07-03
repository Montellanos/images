FROM docker:24.0.2-dind

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="24.0.2-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.42.1

RUN apk add --no-cache python3=3.11.4-r0 \
  py3-pip=23.1.2-r0 \
  wget=1.21.4-r0 \
  jq=1.6-r3

RUN pip3 install awscli==1.27.157

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm trivy.tar.gz


