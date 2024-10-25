# ionic-web-builder

Ubuntu based image to compile ionic web based proyects

docker build . -t unreleaseduser/ionic-web-builder:5.0.3-ubuntu20.04 --no-cache --progress plain

docker tag unreleaseduser/ionic-web-builder:5.0.3-ubuntu20.04 unreleaseduser/ionic-web-builder:5.0.3-ubuntu20.04

docker push unreleaseduser/ionic-web-builder:5.0.3-ubuntu20.04

docker run aquasec/trivy image unreleaseduser/ionic-web-builder:5.0.3-ubuntu20.04 --timeout 20m --db-repository public.ecr.aws/aquasecurity/trivy-db --java-db-repository public.ecr.aws/aquasecurity/trivy-java-db

