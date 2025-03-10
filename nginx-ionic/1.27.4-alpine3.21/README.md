# nginx-ionic

Alpine based image to create containers based on nginx and ionic

docker build . -t unreleaseduser/nginx-ionic:1.27.4-alpine3.21 --no-cache --progress plain

docker tag unreleaseduser/nginx-ionic:1.27.4-alpine3.21 unreleaseduser/nginx-ionic:1.27.4-alpine3.21

docker push unreleaseduser/nginx-ionic:1.27.4-alpine3.21

docker run aquasec/trivy image unreleaseduser/nginx-ionic:1.27.4-alpine3.21 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

