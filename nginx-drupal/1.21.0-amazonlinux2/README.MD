# nginx-drupal
Amazonlinux 2 based image to create containers based on nginx and drupal


docker build . -t unreleaseduser/nginx-drupal:1.21.0-amazonlinux2 

docker tag unreleaseduser/nginx-drupal:1.21.0-amazonlinux2 unreleaseduser/nginx-drupal:1.21.0-amazonlinux2

docker push unreleaseduser/nginx-drupal:1.21.0-amazonlinux2

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.21.0-amazonlinux2 