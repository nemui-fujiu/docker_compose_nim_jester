FROM nginx:latest
MAINTAINER satoshi.fujiu

ADD ./server.conf /etc/nginx/conf.d/default.conf

RUN apt-get update && apt-get install -y vim curl

WORKDIR /opt/nim_server