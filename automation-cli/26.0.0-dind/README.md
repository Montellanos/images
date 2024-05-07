# automation-cli

This image contains minor automation tools for Gitlab CI

docker build . -t unreleaseduser/automation-cli:26.0.0-dind 

docker tag unreleaseduser/automation-cli:26.0.0-dind unreleaseduser/automation-cli:26.0.0-dind

docker push unreleaseduser/automation-cli:26.0.0-dind

docker run aquasec/trivy image unreleaseduser/automation-cli:26.0.0-dind