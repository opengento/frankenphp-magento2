# Magento on FrankenPHP

## Requirements

- [Docker](https://docs.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/overview/)
- [Git](https://git-scm.com/)

## Installation

- copy and **configure** environment files:  
```
cp .env.dist .env
cp ./.docker/database/.env.dist ./.docker/database/.env
cp ./.docker/opensearch/.env.dist ./.docker/opensearch/.env
cp ./.docker/rabbitmq/.env.dist ./.docker/rabbitmq/.env
```
- edit the SERVER_NAME variable in the .env file and replace docker-magento-skeleton.localdev with your domain
- run the docker-compose file: `docker compose up -d --remove-orphans`
- use your composer files to install your project
- edit the file `/etc/hosts` of your machine and add your domain like this :

```
127.0.0.1 docker-magento-skeleton.localdev
```

Install Magento:
```
bin/magento setup:install \
--base-url=https://frankengento.localdev/ \
--db-host=database \
--db-name=magento-database \
--db-user=magento-user \
--db-password=magento-password \
--backend-frontname=admin \
--admin-firstname=Magento \
--admin-lastname=Admin \
--admin-email=admin@example.com \
--admin-user=admin \
--admin-password=Magent0! \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=opensearch \
--opensearch-port=9200 \
--cache-backend redis \
--cache-backend-redis-server redis \
--cache-backend-redis-port 6379 \
--cache-backend-redis-db 0 \
--page-cache=redis \
--page-cache-redis-server redis \
--page-cache-redis-port 6379 \
--page-cache-redis-db=1 \
--session-save=redis \
--session-save-redis-host redis \
--session-save-redis-port 6379 \
--session-save-redis-db 2
```
