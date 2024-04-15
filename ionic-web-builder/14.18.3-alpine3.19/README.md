# ionic-web-builder

Alpine based image to compile ionic web based proyects

docker build . -t unreleaseduser/ionic-web-builder:14.18.3-alpine3.19 

docker tag unreleaseduser/ionic-web-builder:14.18.3-alpine3.19 unreleaseduser/ionic-web-builder:14.18.3-alpine3.19

docker push unreleaseduser/ionic-web-builder:14.18.3-alpine3.19

docker run aquasec/trivy image unreleaseduser/ionic-web-builder:14.18.3-alpine3.19 

