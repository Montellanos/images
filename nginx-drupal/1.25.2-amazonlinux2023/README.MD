# nginx-drupal
Amazonlinux 2023 based image to create containers based on nginx and drupal


docker build . -t unreleaseduser/nginx-drupal:1.25.2-amazonlinux2023 

docker tag unreleaseduser/nginx-drupal:1.25.2-amazonlinux2023  unreleaseduser/nginx-drupal:1.25.2-amazonlinux2023 

docker push unreleaseduser/nginx-drupal:1.25.2-amazonlinux2023 

docker run aquasec/trivy image unreleaseduser/nginx-drupal:1.25.2-amazonlinux2023  