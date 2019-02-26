FROM alpine:3.8

MAINTAINER Honvid, https://github.com/honvid

USER root

RUN apk add --no-cache bash git nodejs npm \
    && ln -sf /usr/share/zoneinfo/Asia/Chongqing /etc/localtime

RUN echo "===> Create Work Path..." \
    && mkdir -p /usr/src/app

RUN cd /tmp \
    && echo "===> Clone Elasticsearch..." \
    && git clone git://github.com/mobz/elasticsearch-head.git \
    && cd elasticsearch-head \
    && cp -r ./ /usr/src/app \
    && rm -rf /tmp/*

WORKDIR /usr/src/app

RUN npm install -g grunt

# COPY package.json /usr/src/app/package.json

RUN npm install

EXPOSE 9100

CMD ["grunt", "server"]