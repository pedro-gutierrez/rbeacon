

# rbeacon -  LAN discovery and presence. #

Copyright (c) 2014 Benoît Chesneau.

__Version:__ 0.3.0

## Description

This is a fork of [rbeacon](https://github.com/refuge/rbeacon), with the following additions:

* Support for UDP unicast. This is to workaround environments where UDP broadcast is not supported (eg. Docker overlay networks).


## Unicast example

By default, the API is backwards compatible with original repo. In order to activate unicast, you can do:

```
{ok, Service} = rbeacon:new(9999, [active, noecho, {unicast, "my-docker-swarm-service"}]),
```

And everything else should work exactly the same as in the default broadcast mode. When working in unicast mode, rbeacon resolves the provided service name into a set of Ip addresses, then sends a UDP message to each one of them. 
