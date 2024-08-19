docker build . -t drupal-database

docker run -d -p 3306:3306 -t drupal-database