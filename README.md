OpenResty (Nginx) -> Lua -> RabbitMQ 
====================================

Task: Send all POST data from nginx to RabbitMQ

Links
- [OpenRasty](https://github.com/openresty/openresty)
- [lua-resty-rabbitmqstomp](https://github.com/wingify/lua-resty-rabbitmqstomp)

How to run:
```bash
docker-compose build && docker-compose up -d
```

How to use:
```bash
curl --header "Content-Type: application/json" \
  --request POST \
  --data '{"foo":"bar","test":1}' \
  http://localhost/rabbitmq
```