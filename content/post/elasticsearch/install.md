---
title: "Elastic Search Installation"
date: 2018-03-03T10:47:04+08:00
draft: false
lastmod: 2018-03-03T10:47:04+08:00
tags: ["Elastic Search"]
categories: ["Elastic Search"]
---

# Installation guide for Mac

Make sure you have `homebrew` installed first!

## Install Java 8

1. `brew tap caskroom/versions`: installing elastic search using homebrew requires Java8...
2. `brew cask install java8`

## Install elastic search

1. `brew install elasticsearch`
2. Run `brew info elasticsearch`, you will see where the data is stored. For example, you will see...

```
Data:    /usr/local/var/lib/elasticsearch/elasticsearch_henrybear327/
Logs:    /usr/local/var/log/elasticsearch/elasticsearch_henrybear327.log
Plugins: /usr/local/var/elasticsearch/plugins/
Config:  /usr/local/etc/elasticsearch/
```
