---
title: "Apache Virtual Host"
date: 2018-02-04T10:48:17+08:00
draft: false
lastmod: 2018-02-04T10:48:17+08:00
tags: ["apache", "virtual host"]
categories: ["Apache"]
---

Setup an Apache virtual host.

<!--more-->

# Setup

The note is extracted from [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04)

* Setup a folder `sudo mkdir -p /var/www/[domian name to use]/html`
* Grant permission `sudo chown -R $USER:$USER /var/www/[domian name to use]/html`
* `sudo chmod -R 755 /var/www`

## Create A Demo Page

Run `vim /var/www/[domian name to use]/html/index.html` and add
```
<html>
  <head>
    <title>Welcome to Example.com!</title>
  </head>
  <body>
    <h1>Success!  The example.com virtual host is working!</h1>
  </body>
</html>
```

# Create A New Virtual Host File

* `sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/[domian name to use].conf`
* `sudo vim /etc/apache2/sites-available/[domian name to use].conf`
* The `.conf` file should look something like this (change `[domian name to use]` according to your needs):

```
<VirtualHost *:80>
         ServerAdmin admin@[domian name to use]
         ServerName [domian name to use]
         ServerAlias www.[domian name to use]
         DocumentRoot /var/www/[domian name to use]/public

         <Directory [path to your site folder]>
                Options -Indexes +FollowSymLinks +MultiViews

                # Allow .htaccess files
                AllowOverride All

                # Allow web access to this directory
                Require all granted
        </Directory>
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

# Enable/Disable the New Virtual Host Files

* `sudo a2ensite [domian name to use].conf`
* `sudo a2dissite 000-default.conf`

# Restart

* `sudo systemctl restart apache2`