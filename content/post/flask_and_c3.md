---
title: "Building a simple website using Flask"
date: 2018-02-03T10:48:17+08:00
draft: true
lastmod: 2018-02-03T10:48:17+08:00
tags: ["python", "flask", "WSGI"]
categories: ["Python", "Flask"]
---

Flask is a really fast and simple framework to use. It's not packed with all sorts of features that you might not need at all, instead, they only give you the essentials. You are free to decide what to do for the rest. 

<!--more-->

# Flask

Simply install with `pip install Flask`, or use virtualenv/conda to install it

Create a `test.py` and paste in the following code

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello World!"

if __name__ == '__main__':
    app.run(debug=True)  
```

Run `python test.py`, you should have a local development server running on `localhost:5000`

## Apache WSGI

For Flask to run on production server using python 3, we need the to install the appropriate WSGI package and configure it properly.

### Installation

* `sudo apt-get install libapache2-mod-wsgi-py3`
* `sudo service apache2 restart`

### Setup

Just like the normal [virtual host]({{< ref "apache_virtualhost.md" >}}) setup, with just one tweak required (WSGIScriptAlias line).

```
<VirtualHost *:80>
    ServerName [site url]

    WSGIScriptAlias / /www/var/my_site/my_site.wsgi
    <Directory /www/var/my_site/>
        ...
    </Directory>

</VirtualHost>
```

Only WSGIScriptAlias is specific to WSGI. WSGIScriptAlias tells the ULR path “/” should be handled by a Python program  `/www/var/my_site/my_site.wsgi`. 

### `.WSGI` file

Setting up this file is another painful story. Read [this](http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/#creating-a-wsgi-file)

### Debugging

* The default Apache2 server on Ubunut should have its error log at `/var/log/apache2/error.log`. When receiving internal error 500 or any sort of failures during development, you can simply go to error log and see what went wrong.
* One of the main issue of developing Flask applications might be the webpage simply kept showing the old version instead of the new one. The issue is explained clearly [here](http://modwsgi.readthedocs.io/en/develop/user-guides/reloading-source-code.html). It's not a bug. 
    * Dirty workaround: add `MaxRequestsPerChild 1` to `/etc/apache2/apache2.conf`, and then `service apache2 restart`

# Jetbrain Pycharm Professional

直接支援 Flask 和 virtualenv/conda! 這真的太讚了~
