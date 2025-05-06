## Defining The Environment

docker build -t myclient:latest . 

docker images

docker run -it myclient:latest /bin/sh

/# apk update
/# apk add --update nodejs npm
/# apk add nodejs 
/# apk add --update npm
/# node -v
/# exit

curl -sS https://getcomposer.org/installer >> composer-setup.php

sha384sum composer-setup.php

docker build -t myserver:latest . 

## Installing React

docker run -it --mount type=bind,source="$(pwd)"/client,target=/usr/src/app myclient:latest /bin/sh

/# cd /usr/src
/# npx create-react-app client ; mv client/* app/ ; rm -rf client
/# cd /app ; npm install
/# exit

## Installing Laravel

docker run -it --mount type=bind,source="$(pwd)"/server,target=/var/www myserver:latest /bin/sh

/# cd /var/# composer global update
/# composer create-project --prefer-dist laravel/laravel server ; mv server/* www/ ; rm -rf server
/# cd www ; chmod -R 775 storage
/# wget https://raw.githubusercontent.com/laravel/laravel/refs/heads/master/.env.example
/# cp .env.example .env
/# php artisan key:generate
/# exit

## Run Client & Server
$ docker run -p 80:3000 --mount src=client,target=/usr/src/app myclient:latest npm start
$ docker run -p 9000:80 --mount src=server,target=/var/www myserver:latest

## Alternative to Running Client & Server
docker-compose up
docker-compose down
