# Day 07

## Install mongoDB and Robo-3T
1. [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/)
2. [Robo-3T](http://larrynung.github.io/2019/06/25/Robo-3T-Install-with-HomeBrew/)

## Practice mongoDB

* **Using Shell**
```shell
$ use Member
$ db.member.insert({"name": "Kevin", "email": "test@abc.com", "phone": 0921345678})
$ db.member.update({"name": "Kevin"}, {$set : {"name": "Cathy"}})
$ db.member.update({"name": "Cathy"}, {$set : {"age": 25}}
```
* **Using Robo-3T**
    > Use the mouse click.