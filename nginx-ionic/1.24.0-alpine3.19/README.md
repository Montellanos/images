# nginx-ionic

Alpine based image to create containers based on nginx and ionic

docker build . -t unreleaseduser/nginx-ionic:1.24.0-alpine3.19 --no-cache --progress plain

docker tag unreleaseduser/nginx-ionic:1.24.0-alpine3.19 unreleaseduser/nginx-ionic:1.24.0-alpine3.19

docker push unreleaseduser/nginx-ionic:1.24.0-alpine3.19

docker run aquasec/trivy image unreleaseduser/nginx-ionic:1.24.0-alpine3.19 --timeout 20m

