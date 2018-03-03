---
title: "Elastic Search Installation"
date: 2018-03-03T10:47:04+08:00
draft: false
lastmod: 2018-03-03T10:47:04+08:00
tags: ["Elastic Search"]
categories: ["Elastic Search"]
---

Elastic search installation notes

<!--more-->

#  Install Elastic Search on Mac

Make sure you have `homebrew` installed first!

## Install Java 8

1. `brew tap caskroom/versions`: installing elastic search using homebrew requires Java8...
2. `brew cask install java8`

## Install Elastic Search

1. `brew install elasticsearch`
2. Run `brew info elasticsearch`, you will see where the data is stored. For example, you will see...

```text
Data:    /usr/local/var/lib/elasticsearch/elasticsearch_henrybear327/
Logs:    /usr/local/var/log/elasticsearch/elasticsearch_henrybear327.log
Plugins: /usr/local/var/elasticsearch/plugins/
Config:  /usr/local/etc/elasticsearch/
```

## Start Elastic Search

Simply run `elasticsearch` in the terminal, you will see a lot of messages being thrown to your screen.

Wait for a while until you see something like this...

```text
[2018-03-03T11:02:49,111][INFO ][o.e.h.n.Netty4HttpServerTransport] [FOq2ljA] publish_address {127.0.0.1:9200}, bound_addresses {[::1]:9200}, {127.0.0.1:9200}
```

You are good to go!

# Elastic Search Usages

## Python API

We will use [elasticsearch-py](https://www.elastic.co/guide/en/elasticsearch/client/python-api/current/index.html).

1. Setup virtual environment: `virtualenv venv`, or use conda if you wish
2. `source venv/bin/activate`
3. `pip install elasticsearch`

Read the [documentation](http://elasticsearch-py.readthedocs.io/en/master/)
