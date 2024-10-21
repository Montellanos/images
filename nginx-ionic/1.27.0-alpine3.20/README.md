# nginx-ionic

Alpine based image to create containers based on nginx and ionic

docker build . -t unreleaseduser/nginx-ionic:1.27.0-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/nginx-ionic:1.27.0-alpine3.20 unreleaseduser/nginx-ionic:1.27.0-alpine3.20

docker push unreleaseduser/nginx-ionic:1.27.0-alpine3.20

docker run aquasec/trivy image unreleaseduser/nginx-ionic:1.27.0-alpine3.20 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

