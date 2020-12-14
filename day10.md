---
tags: AIOT
---

# Day10

## Installer MongoDB on docker
```shell
# Pull the docker image form docker hub
$ docker pull mongo:latest

# Check the download images
$ docker images

# Activate the container and connect from port 27017
$ docker run -itd --name mongo -p 27017:27017 mongo --auth
```

## Create root user
```shell
# Enter mongo shell
$ docker exec -it mongo mongo

> use admin
> db.createUser(
       {
        user: 'admin',
        pwd: 'your-password',
        roles: [ { role: 'root', db: 'admin' } ]
      }
    )
```

## Connect from outside of the container
```shell
# Enter bash
$ docker exec -it mongo bash

# Open the connection
$ mongo --port 27017 -u "<user-name>" -p "<password>" --authenticationDatabase "admin" 
```

* Result
    ![](https://i.imgur.com/6OzMsiK.png)
