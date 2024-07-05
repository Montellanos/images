# Ruby builder

Alpine based image to build proyects with ruby

docker build . -t unreleaseduser/ruby-builder:3.3.3-alpine3.20 --no-cache --progress plain

docker tag unreleaseduser/ruby-builder:3.3.3-alpine3.20 unreleaseduser/ruby-builder:3.3.3-alpine3.20

docker push unreleaseduser/ruby-builder:3.3.3-alpine3.20

docker run aquasec/trivy image unreleaseduser/ruby-builder:3.3.3-alpine3.20 --timeout 20m

