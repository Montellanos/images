# automation-cli

This image contains minor automation tools for Gitlab CI

docker build . -t unreleaseduser/automation-cli:26.1.3-dind --no-cache --progress plain

docker tag unreleaseduser/automation-cli:26.1.3-dind unreleaseduser/automation-cli:26.1.3-dind

docker push unreleaseduser/automation-cli:26.1.3-dind

docker run aquasec/trivy image unreleaseduser/automation-cli:26.1.3-dind --timeout 20m
