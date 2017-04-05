# Install Sensu Core


* Configure sensu:
```
# This is the file config for rabbitmq connection
$ cat /etc/sensu/conf.d/rabbitmq.json
{
  "rabbitmq": {
    "host": "x.x.x.x", # Host where is installed Rabbit
    "port": 5672,
    "vhost": "/sensu",
    "user": "sensu",
    "password": "secret"
  }
}
# The api is for server-api, who connect yo redis and rabbitmq
$ cat /etc/sensu/conf.d/api.json
{
  "api": {
    "host": "localhost",
    "bind": "0.0.0.0",
    "port": 4567
  }
}
# This is the config client for itselft monitoring
$ cat /etc/sensu/conf.d/client.json
{
  "client": {
    "name": "localhost",
    "address": "127.0.0.1",
    "enviroment": "test",
    "subscriptions": [
      "test"
    ],
  "socket": {
    "bind": "127.0.0.1",
    "port": 3030
    }
  }
}
# This is the file config for redis connection
$ cat /etc/sensu/conf.d/redis.json
{
  "redis": {
    "host": "x.x.x.x",
    "port": 6379,
    "auto_reconnect": true
  }
}
# This setting tells to sensu which transport to use
$ cat /etc/sensu/conf.d/transport.json
{
  "transport": {
    "name": "rabbitmq",
    "reconnect_on_error": true
  }
}
```


