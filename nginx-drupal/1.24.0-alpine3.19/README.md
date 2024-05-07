# nginx-drupal

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/nginx-drupal:1.24.0-alpine3.19 

docker tag unreleaseduser/nginx-drupal:1.24.0-alpine3.19 unreleaseduser/nginx-drupal:1.24.0-alpine3.19

docker push unreleaseduser/nginx-drupal:1.24.0-alpine3.19

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.24.0-alpine3.19 

