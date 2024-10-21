# nginx

Alpine based image to create containers based on nginx

docker build . -t unreleaseduser/nginx:1.26.2-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/nginx:1.26.2-alpine3.20 unreleaseduser/nginx:1.26.2-alpine3.20

docker push unreleaseduser/nginx:1.26.2-alpine3.20

docker run aquasec/trivy image unreleaseduser/nginx:1.26.2-alpine3.20 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db
