# Install RabbitMQ

In the dockerfile there are the instruction for installing rabbit. 
Is automatic.
Them, you need to do the next tasks.

* Enable the service and start it.
```
$ systemctl enable rabbitmq-server
$ systemctl start rabbitmq-server
```
* Create vhost and user
```
$ rabbitmqctl add_vhost /sensu
$ rabbitmqctl add_user sensu secret
$ rabbitmqctl set_permissions -p /sensu sensu ".*" ".*" ".*"
```
_Uncoment ulimit line in etc/default/rabbitmq-server and set to 4096 for test
To verify that the RabbitMQ open file handle limit has been increase, please run:_
```
$ rabbitmqctl status
```

##  Next steps are 
- [ ] Add the enable and start command to dockerfile
- [ ] Migrate dockerfile to compose
- [ ] Mount volume to persist data
