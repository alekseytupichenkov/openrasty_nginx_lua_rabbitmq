FROM openresty/openresty:jessie

RUN apt-get update && \
    apt-get install -y openssh-client git && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/wingify/lua-resty-rabbitmqstomp.git /rabbitmqstomp

COPY nginx.conf /usr/local/openresty/nginx/conf/nginx.conf

RUN cd /rabbitmqstomp && make install