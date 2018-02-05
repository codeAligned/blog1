---
title: "SSHFS"
date: 2018-02-02T08:40:30+08:00
draft: false
lastmod: 2018-02-02T08:40:30+08:00
tags: ["ssh"]
categories: ["OSX"]
---

Mount your remote host's folders onto local filesystem!

<!--more-->

## Installation

1. `brew cask install osxfuse`
2. `brew install sshfs`

## Usage

Create a directory by using `mkdir` (mount point for sshfs)

* Mounting: `sshfs username@host:/path/to/folder/on/remote /path/to/folder/you/just/created`
* Umounting: `umount /path/to/folder/you/just/created`
