FROM rabbitmq:3.7-management

RUN rabbitmq-plugins enable --offline rabbitmq_stomp

ADD rabbitmq.config /etc/rabbitmq/
ADD definitions.json /etc/rabbitmq/

EXPOSE 61613
