# promtail

Alpine based image to create listener containers with promtail

docker build . -t unreleaseduser/promtail:2.9.4-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/promtail:2.9.4-alpine3.20 unreleaseduser/promtail:2.9.4-alpine3.20

docker push unreleaseduser/promtail:2.9.4-alpine3.20

docker run aquasec/trivy image unreleaseduser/promtail:2.9.4-alpine3.20 --timeout 20m

