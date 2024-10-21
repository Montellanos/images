# spring-web

Alpine based image to expose spring web based proyects

docker build . -t unreleaseduser/spring-web:22.0.1-alpine3.19 --no-cache --progress plain

docker tag unreleaseduser/spring-web:22.0.1-alpine3.19 unreleaseduser/spring-web:22.0.1-alpine3.19

docker push unreleaseduser/spring-web:22.0.1-alpine3.19

docker run aquasec/trivy image unreleaseduser/spring-web:22.0.1-alpine3.19 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

