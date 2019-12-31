Docker-Compose enabled Laravel test app


## Install Docker
sudo apt update -y

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" -y

sudo apt update -y

sudo apt install docker-ce -y

sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose


## Clone this repo
cd ~

git clone https://github.com/bealbrown/laratest.git


## Initalize
cd ~/laratest

docker run --rm -v $(pwd):/app composer install

sudo chown -R $USER:$USER ~/laratest

docker-compose exec app nano .env

cp .env.example .env

docker-compose up -d

docker ps

docker-compose exec app php artisan key:generate

docker-compose exec app php artisan config:cache

docker-compose exec db bash

docker-compose exec app php artisan migrate

docker-compose exec app php artisan tinker

