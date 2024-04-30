docker build . -t drupal-redis

docker run -d -p 6379:6379 -t drupal-redis