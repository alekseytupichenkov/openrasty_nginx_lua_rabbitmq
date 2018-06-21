OpenResty (Nginx) -> Lua -> RabbitMQ 
====================================

Task: Wrire post data to RabbitMQ through OpenResty (nginx + lua)

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

Performance test, all running on my Mac using docker, so it's not so fast :)
When I'll deploy this to production server, I'll write about performance on it
```bash
ab -T 'application/json' -n 1000 -p post.json http://127.0.0.1/rabbitmq
This is ApacheBench, Version 2.3 <$Revision: 1826891 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 127.0.0.1 (be patient)
Completed 100 requests
Completed 200 requests
Completed 300 requests
Completed 400 requests
Completed 500 requests
Completed 600 requests
Completed 700 requests
Completed 800 requests
Completed 900 requests
Completed 1000 requests
Finished 1000 requests


Server Software:        openresty/1.13.6.1
Server Hostname:        127.0.0.1
Server Port:            80

Document Path:          /rabbitmq
Document Length:        17 bytes

Concurrency Level:      1
Time taken for tests:   1.465 seconds
Complete requests:      1000
Failed requests:        0
Total transferred:      185000 bytes
Total body sent:        160000
HTML transferred:       17000 bytes
Requests per second:    682.62 [#/sec] (mean)
Time per request:       1.465 [ms] (mean)
Time per request:       1.465 [ms] (mean, across all concurrent requests)
Transfer rate:          123.33 [Kbytes/sec] received
                        106.66 kb/s sent
                        229.99 kb/s total

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.0      0       1
Processing:     1    1   0.8      1      17
Waiting:        1    1   0.8      1      17
Total:          1    1   0.8      1      17

Percentage of the requests served within a certain time (ms)
  50%      1
  66%      1
  75%      1
  80%      2
  90%      2
  95%      2
  98%      2
  99%      3
 100%     17 (longest request)
```
