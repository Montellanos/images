# node

Alpine based image to create containers based on nginx and drupal

docker build . -t unreleaseduser/node:20.15.1-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/node:20.15.1-alpine3.20 unreleaseduser/node:20.15.1-alpine3.20

docker push unreleaseduser/node:20.15.1-alpine3.20

docker run aquasec/trivy image unreleaseduser/node:20.15.1-alpine3.20 --timeout 20m
