ARG NGINX_VERSION=1.19
FROM nginx:${NGINX_VERSION}

LABEL author.name = "Evgeniy Terin"
LABEL author.email = "web@derin.ru"

ADD ./config.conf /etc/nginx/conf.d/config.conf

ARG TIMEZONE="Europe/Moscow"
ENV TZ=${TIMEZONE}

WORKDIR /var/www