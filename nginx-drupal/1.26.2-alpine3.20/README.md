# nginx-drupal

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/nginx-drupal:1.26.2-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/nginx-drupal:1.26.2-alpine3.20 unreleaseduser/nginx-drupal:1.26.2-alpine3.20

docker push unreleaseduser/nginx-drupal:1.26.2-alpine3.20

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.26.2-alpine3.20 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
