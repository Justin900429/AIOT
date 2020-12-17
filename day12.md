---
tags: AIOT
---

# Day12

## Change the password
```shell
$ sudo raspi-config
```

![](https://i.imgur.com/XJNKLHt.png)

## Download the file to /opt/aiot
```shell
$ cd /opt
$ sudo mkdir aiot
$ sudo wget https://github.com/Justin900429/AIOT/blob/master/day11.md
```



## Backup the /opt file
```shell
$ sudo tar zcvf opt.tar.gz /opt
$ sudo bzip2 opt.tar.gz
$ sudo tar zxvf opt.tar.gz /tmp
```

