---
title: "Share documents between VM and Windows"
date: 2018-03-08T22:21:01+08:00
draft: false
lastmod: 2018-03-08T22:21:01+08:00
tags: ["samba", "VMWare"]
categories: ["VMWare"]
---

<!--more-->

# Setup Samba

Assuming that the OS running in VM is Ubuntu, and the host OS is Windows.

* Install Samba: `sudo apt install samba`
* Add current user as Samba user: `sudo smbpasswd -a $USER`
* Run `sudo vim /etc/samba/smb.conf`, and add the following configs to it

```
[global]
# Let Samba share follow symbolic links 
follow symlink = yes
wide symlinks = yes
unix extensions = no

[homes]
comment = Home Directories
browseable = no
valid users = %S
writable = yes
create mask = 0664
directory mask = 0775
```

* Restart samba `sudo /etc/init.d/samba restart`
* Check if the config file is loaded correctly `sudo testparm`

# Mount disk on Windows

1. Run `ifconfig` in the VM and copy the ip of `Link encap:Ethernet` out.
2. On Windows, mount the drive by entering `\\VM-ip\username-in-your-VM` to connect

That's it!