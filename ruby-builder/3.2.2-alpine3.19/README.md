# Ruby builder

Alpine based image to build proyects with ruby

docker build . -t unreleaseduser/ruby-builder:3.2.2-alpine3.19 --no-cache --progress plain

docker tag unreleaseduser/ruby-builder:3.2.2-alpine3.19 unreleaseduser/ruby-builder:3.2.2-alpine3.19

docker push unreleaseduser/ruby-builder:3.2.2-alpine3.19

docker run aquasec/trivy image unreleaseduser/ruby-builder:3.2.2-alpine3.19 --timeout 20m

