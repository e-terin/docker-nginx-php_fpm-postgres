ARG POSTGRESS_VERSION=14
FROM postgres:${POSTGRESS_VERSION}
RUN localedef -i ru_RU -c -f UTF-8 -A /usr/share/locale/locale.alias ru_RU.UTF-8
ENV LANG ru_RU.utf8

ARG TIMEZONE="Europe/Moscow"
ENV TZ=${TIMEZONE}