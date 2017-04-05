# Sensu
## Howto, install, tests and more about Sensu

In this repository I'll add documents, files, and templates for install Sensu Distribuited.

## Thinks to keep in mind

You can see the _Sensu_ arquitecture in the [website](https://sensuapp.org/docs/0.28/overview/architecture.html)
to understand the installation steps.

I couldn't get all explanations in the documents pages on Sensu Website, 
so I let some notes about conf files and how to sort it.

When you install Sensu you install the _core server_, that bring with it the Server,
the Api and the Client and you'll can enable the three components or the Server and the Api or only the Client, it depends on which config files you will setup.
So, the conf directory is the same for all de components. 
The change is in the directive in the json config file.
Therefore, in the next, we describe you which files you need setup for.

### Sensu Server

Configuration Files Directory:

* `/etc/sensu/conf.d/`

Files:

* `redis.json` > Config for strings connections to redis (data).
* `rabbitmg.json` > Config for strings connections to rabbitmq (transport).
* `transport.json` > All of the Sensu processes require configuration to tell them how to connect to the configured transport.
* `[plugin].json` > Whatever plugin installed (sensu-install) need a config file in the server.

### Sensu Api

* `api.json` > Config for string connections to the api server.

### Sensu Client

* `client.json` > Config for strings to clients connections.

_Note: This config file could be ambiguous, because it's setting up in the hosts clients and in the sensu server, as agent monitoring for a standar and navite sensu setup and monitoring (see documentation) or if you want to reuse the Nagios Plugins you only add the host in the client config in the Sensu Server.


### Uchiwa Dashboard

Configuration Files Directory:

* `/etc/sensu/`

Files: 

* `uchiwa.json` > Config for setting up the uchiwa dashboard and _datacenters_

## Troubleshotting

## Notes

1. Debian Docker
* Problems on install sensu suite
2. CentOS Docker
* Problems on install sensu suite


