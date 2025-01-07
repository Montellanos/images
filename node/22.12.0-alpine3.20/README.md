# node

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/node:22.12.0-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/node:22.12.0-alpine3.20 unreleaseduser/node:22.12.0-alpine3.20

docker push unreleaseduser/node:22.12.0-alpine3.20

docker run aquasec/trivy image unreleaseduser/node:22.12.0-alpine3.20 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
