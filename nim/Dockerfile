FROM nimlang/nim:latest
MAINTAINER satoshi.fujiu

RUN apt-get update && apt-get install -y vim curl

RUN nimble -y install jester


WORKDIR /opt/nim_jester

