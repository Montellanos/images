FROM --platform=linux/amd64 alpine:3.20.1

LABEL maintainer="Jorge Montellanos Díaz"
LABEL description="Alpine based image to create listener containers with promtail"
LABEL version="2.9.4-alpine3.20"
LABEL license="Apache License 2.0"

ENV PROMTAIL_VERSION=2.9.4-r6

RUN apk update && apk add --no-cache \
  libcrypto3=3.3.1-r1 \
  libssl3=3.3.1-r1 \
  loki-promtail=${PROMTAIL_VERSION} 

EXPOSE 9080

ENTRYPOINT ["promtail"]