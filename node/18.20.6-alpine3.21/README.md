# node

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/node:18.20.6-alpine3.21 --no-cache --progress plain

docker tag unreleaseduser/node:18.20.6-alpine3.21 unreleaseduser/node:18.20.6-alpine3.21

docker push unreleaseduser/node:18.20.6-alpine3.21

docker run aquasec/trivy image unreleaseduser/node:18.20.6-alpine3.21 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
