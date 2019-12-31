
## Clone this repo
cd ~

git clone https://github.com/bealbrown/laratest.git



## Install Docker
chmod +x install_docker

./install_docker


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

