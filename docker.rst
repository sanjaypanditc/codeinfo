.. _docker:

Docker
==============

docker build -f Dockerfile .

docker run -i -t -p 80:80 4214bb0c53d2 /bin/bash
apachectl start

docker build \
  --file .docker/Dockerfile \
  -t sanjaydocker .

docker run --rm -p 8080:80 sanjaydocker

ssh -i /home/admin1/Desktop/your.pem ubuntu@yourip
sudo apt-get install docker docker-compose
sudo docker-compose up


docker-compose down && docker-compose up -d 

1) Clone the repository using the master branch 
2) Run git checkout docker 
3) Run docker-compose -f docker-compose-nginx.yml up -d 
4) Run docker-compose down && docker-compose up -d 