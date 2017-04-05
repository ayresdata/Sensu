# Install Uchiwa


> See: https://docs.uchiwa.io/getting-started/installation/
     https://docs.uchiwa.io/getting-started/configuration/
     https://sensuapp.org/docs/0.24/platforms/sensu-on-ubuntu-debian.html#sensu-core

In the dockerfile there are the instruction for installing rabbit. 
Is automatic.
Them, you need to do the next tasks.

* Config
```
$ cat /etc/sensu/uchiwa.json
{
  "sensu": [
    {
      "name": "Site 1",
      "host": "test.example.com",
      "port": 4567,
      "timeout": 10
    },
    {
      "name": "Site 2",
      "host": "api2.example.com",
      "port": 4567,
      "ssl": false,
      "path": "",
      "user": "",
      "pass": "",
      "timeout": 10
    }
  ],
  "uchiwa": {    # this block is for setting which IP and Port will run the dashboard
    "host": "0.0.0.0", # This mean "All" interfaces, I'll changes it to 127.0.0.1
    "port": 3000,
    "refresh": 10
  }
}
$ sudo service uchiwa start
$ sudo systemctl enable uchiwa.service
Synchronizing state for uchiwa.service with sysvinit using update-rc.d...
Executing /usr/sbin/update-rc.d uchiwa defaults
Executing /usr/sbin/update-rc.d uchiwa enable
```

## Configure Sensu client

> If you are behind a proxy server, you'll need modify the sensu-intall script and add the proxy info for gem_

* Edit de file /opt/sensu/embedded/lib/ruby/gems/2.3.0/gems/sensu-0.28.4/exe/sensu-install line 65
and add de --http-proxy. i.e
```
gem_command = "gem install --http-proxy http://x.x.x.x:8080 #{gem_name}"
```

## Sensu Plugins (i.e)

> http://sensu-plugins.io/plugins/
> http://sensu-plugins.io/docs/installation_instructions.html

e.g

```
$ sudo sensu-install -v -p check-sftp
[sudo] password for cepxio:
[SENSU-INSTALL] installing Sensu plugins ...
[SENSU-INSTALL] provided Sensu plugins: ["check-sftp"]
[SENSU-INSTALL] compiled Sensu plugin gems: ["sensu-plugins-check-sftp"]
[SENSU-INSTALL] determining if Sensu gem 'sensu-plugins-check-sftp' is already installed ...
[SENSU-INSTALL] gem list -i sensu-plugins-check-sftp
```
```
$ sudo sensu-install -vp check-disk-usage
[SENSU-INSTALL] installing Sensu plugins ...
[SENSU-INSTALL] provided Sensu plugins: ["check-disk-usage"]
[SENSU-INSTALL] compiled Sensu plugin gems: ["sensu-plugins-check-disk-usage"]
[SENSU-INSTALL] determining if Sensu gem 'sensu-plugins-check-disk-usage' is already installed ...
[SENSU-INSTALL] gem list -i sensu-plugins-check-disk-usage
```
