# ionic-web-builder

Ubuntu based image to compile ionic web based proyects

docker build . -t unreleaseduser/ionic-web-builder:5.0.3-alpine3.14 --no-cache --progress plain

docker tag unreleaseduser/ionic-web-builder:5.0.3-alpine3.14 unreleaseduser/ionic-web-builder:5.0.3-alpine3.14

docker push unreleaseduser/ionic-web-builder:5.0.3-alpine3.14

docker run aquasec/trivy image unreleaseduser/ionic-web-builder:5.0.3-alpine3.14 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

