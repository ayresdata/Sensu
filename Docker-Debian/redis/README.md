# Install Redis

In the dockerfile there are the instruction for installing redis.
Them, you need to do the next tasks.

```
$ systemctl enable redis-server
$ systemctl start redis-server
# Test redis-server
$ redis-cli ping
PONG
```

##  Next steps are 
- [ ] Add the enable and start command to dockerfile
- [ ] Migrate dockerfile to compose
- [ ] Mount volume to persist data

> Note: Verify config file for IP, port and limit open files in /etc/redis/redis.conf_
