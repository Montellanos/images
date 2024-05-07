# nginx-drupal

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/nginx-drupal:1.20.2-alpine3.15 

docker tag unreleaseduser/nginx-drupal:1.20.2-alpine3.15 unreleaseduser/nginx-drupal:1.20.2-alpine3.15

docker push unreleaseduser/nginx-drupal:1.20.2-alpine3.15

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.20.2-alpine3.15 