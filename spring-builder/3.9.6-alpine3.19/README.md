# spring-builder

Alpine based image to compile spring based proyects

docker build . -t unreleaseduser/spring-builder:3.9.6-alpine3.19 --no-cache --progress plain

docker tag unreleaseduser/spring-builder:3.9.6-alpine3.19 unreleaseduser/spring-builder:3.9.6-alpine3.19

docker push unreleaseduser/spring-builder:3.9.6-alpine3.19

docker run aquasec/trivy image unreleaseduser/spring-builder:3.9.6-alpine3.19 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

