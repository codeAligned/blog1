---
title: "Install QT 4.8.6 on Linux"
date: 2018-02-19T22:19:29+08:00
draft: false
lastmod: 2018-02-19T22:19:29+08:00
tags: ["QT"]
categories: ["QT"]
---

# Get files

1. [QT source code](http://download.qt.io/archive/qt/4.8/4.8.6/qt-everywhere-opensource-src-4.8.6.tar.gz)
2. [QT Creator](http://download.qt.io/archive/qtcreator/2.5/qt-creator-linux-x86_64-opensource-2.5.2.bin)

# Installation

## QT compiler

1. Install `sudo apt install libx11-dev libxext-dev libxtst-dev`
	* For solving `Basic XLib functionality test failed` error
2. `tar xzvf qt-everywhere-opensource-src-4.8.6.tar.gz`
3. `cd qt-everywhere-opensource-src-4.8.6`
4. `./configure && make && sudo make install`
5. In your `.zshrc`, add

```bash
export QTDIR=/usr/local/Trolltech/Qt-4.8.6   
export PATH=$QTDIR/bin:$PATH   
export MANPATH=$QTDIR/man:$MANPATH   
export LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH 
```

## QT creator

1. `chmod +x qt-creator-linux-x86-opensource-2.5.2.bin`
2. `./qt-creator-linux-x86-opensource-2.5.2.bin`

# Try it!

1. Go to `cd /usr/local/Trolltech/Qt-4.8.6/bin` and execute `./qmake -v`. If you see the version information, you are done!
3. Try typing `qmake` directly in your terminal. If error message occurs, use `which qmake` to locate the soft link and fix it accordingly.