docker build . -t unreleaseduser/automation-cli:24.0.2-dind 

docker tag unreleaseduser/automation-cli:24.0.2-dind unreleaseduser/automation-cli:24.0.2-dind

docker push unreleaseduser/automation-cli:24.0.2-dind