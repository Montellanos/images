# node

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/node:16.20.2-alpine3.18 --no-cache --progress plain

docker tag unreleaseduser/node:16.20.2-alpine3.18 unreleaseduser/node:16.20.2-alpine3.18

docker push unreleaseduser/node:16.20.2-alpine3.18

docker run aquasec/trivy image unreleaseduser/node:16.20.2-alpine3.18 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
