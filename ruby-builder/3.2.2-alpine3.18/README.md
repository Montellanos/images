# Ruby builder

Alpine based image to build proyects with ruby

docker build . -t unreleaseduser/ruby-builder:3.2.2-alpine3.18 --no-cache --progress plain

docker tag unreleaseduser/ruby-builder:3.2.2-alpine3.18 unreleaseduser/ruby-builder:3.2.2-alpine3.18

docker push unreleaseduser/ruby-builder:3.2.2-alpine3.18

docker run aquasec/trivy image unreleaseduser/ruby-builder:3.2.2-alpine3.18 --timeout 20m

