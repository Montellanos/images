# promtail

Alpine based image to create listener containers with promtail

docker build . -t unreleaseduser/promtail:3.3.0-alpine3.21 --no-cache --progress plain

docker tag unreleaseduser/promtail:3.3.0-alpine3.21 unreleaseduser/promtail:3.3.0-alpine3.21

docker push unreleaseduser/promtail:3.3.0-alpine3.21

docker run aquasec/trivy image unreleaseduser/promtail:3.3.0-alpine3.21 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

