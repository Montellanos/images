# nginx-drupal

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/nginx-drupal:1.24.0-alpine3.19 --no-cache --progress plain

docker tag unreleaseduser/nginx-drupal:1.24.0-alpine3.19 unreleaseduser/nginx-drupal:1.24.0-alpine3.19

docker push unreleaseduser/nginx-drupal:1.24.0-alpine3.19

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.24.0-alpine3.19 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
