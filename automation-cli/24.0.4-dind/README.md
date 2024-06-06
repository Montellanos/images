# automation-cli

This image contains minor automation tools for Gitlab CI

docker build . -t unreleaseduser/automation-cli:24.0.4-dind --no-cache --progress plain

docker tag unreleaseduser/automation-cli:24.0.4-dind unreleaseduser/automation-cli:24.0.4-dind

docker push unreleaseduser/automation-cli:24.0.4-dind

docker run aquasec/trivy image unreleaseduser/automation-cli:24.0.4-dind --timeout 20m