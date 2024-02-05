FROM docker:25.0.2-dind

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="This image contains minor automation tools for Gitlab CI"
LABEL version="25.0.2-dind"
LABEL license="Apache License 2.0"

ENV TRIVY_VERSION=0.49.0

RUN apk add --no-cache \
  wget=1.21.4-r0 \
  jq=1.7.1-r0 \
  aws-cli=2.13.25-r0

RUN wget --no-verbose https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-64bit.tar.gz -O trivy.tar.gz \
  && tar -xvf trivy.tar.gz \
  && mkdir /usr/local/templates  \
  && mv contrib /usr/local/templates/ \
  && mv trivy /usr/local/bin/trivy \
  && rm trivy.tar.gz
