---
title: "Python Virtual Environment"
date: 2018-02-04T10:58:36+08:00
draft: false
lastmod: 2018-02-04T10:58:36+08:00
tags: ["python", "virtual environment", "pip", "conda", "virtualenv"]
categories: ["python"]
---

Some notes on virtual environment for Python. Dependency management with ease.

<!--more-->

# Virtual environment

Usually it's about choosing between `virtualenv` + `pip` or `conda`.

The [site](http://stuarteberg.github.io/conda-docs/_downloads/conda-pip-virtualenv-translator.html) has a great table on comparing the differences between them.

## `virtualenv` + `pip`

First we setup `virtualenv`, and after activating it, we install packages in it using normal `pip` operations.

### `virtualenv`

* create: `cd $ENV_BASE_DIR; virtualenv $ENVIRONMENT_NAME`
* activate: `source $ENV_BASE_DIR/$ENVIRONMENT_NAME/bin/activate`
* deactivate: `deactivate`
* install: Normal `pip` operations (Regardless of whether you are using Python 2 or Python 3, when the virtual environment is activated, we should use the `pip` command (not `pip3`))

### `pip`

* install package: `pip install $PACKAGE_NAME`
* upgrade package: `pip install --upgrade $PACKAGE_NAME`
* uninstall package: `pip uninstall $PACKAGE_NAME`
* search package: `pip search $SEARCH_TERM`
* upgrade `pip`: `pip install -U pip`
* list: `pip list`
* generate requirement file (for installation): `pip freeze`

## `conda`

Conda does it all! No separate commands, they are all-in-one.

* create: `conda create -n $ENVIRONMENT_NAME python[=3.6]`
* activate: `source activate $ENVIRONMENT_NAME`
* deactivate: `source deactivate`
* install package: `conda install $PACKAGE_NAME`
* upgrade package: `conda update --name $ENVIRONMENT_NAME $PACKAGE_NAME`
* uninstall package: `conda remove --name $ENVIRONMENT_NAME $PACKAGE_NAME`
* search package: `conda search $SEARCH_TERM`
* upgrade `pip`: `conda update conda`
* list: `conda list --name $ENVIRONMENT_NAME`
* generate requirement file (for installation): `conda list --export`
* list envs: `conda info --envs`
* install python: `conda install python=x.x`
* upgrade python: `conda update python *`