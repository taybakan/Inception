LOGIN			:= taybakan
COMPOSE			:= srcs/docker-compose.yml

all: srcs/.env up

up:
	docker-compose -f $(COMPOSE) up --build --detach

down:
	docker-compose -f $(COMPOSE) down

config:
	docker-compose -f $(COMPOSE) config

srcs/.env:
	@echo "Missing .env file in srcs folder" && exit 1

fprune:
	docker system prune --all --force --volumes

setup: srcs/.env
	mkdir -p /home/taybakan/data/wordpress
	mkdir -p /home/taybakan/data/mariadb
	grep $(LOGIN).42.fr /etc/hosts || echo "127.0.0.1 $(LOGIN).42.fr" >> /etc/hosts
	grep VOLUMES_PATH srcs/.env || echo "VOLUMES_PATH=/home/taybakan/data" >> srcs/.env
