---
tags: AIOT
---

# Day09

## Docker file

### Build the MongoDB
Using the [mongoDB Dockerfile](https://github.com/docker-library/mongo/blob/master/4.4/Dockerfile).

```shell
# Under the build folder
$ docker build --tag mongo_share:1.0 .

# Run the image
$ docker run -p 27017:27017 --name mongo_share -d mongo
```

<img src="https://i.imgur.com/PwpLs1R.png" width=350 />

### Test the docker image

```python
from pymongo import MongoClient

# Connect to the mongo server
client = MongoClient(host='127.0.0.1', port=27017)

# Create new database
mydb = client["test_mongo_docker"]

# Create new collection
mycol = mydb["test"]

# Insert a datum
mycol.insert_one({"name": "Jason"})

# Print data
result = mycol.find({})
print(result[0])
```

```shell
{'_id': ObjectId('5fd5bc1da57b259b6d4ef33a'), 'name': 'Jason'}
```

### Push the docker image
```shell
# Tag the image
$ docker tag 8d4 justin0429/mongo_share:test

# Push the image
$ docker push justin0429/mongo_share:test
```

![](https://i.imgur.com/UksszWN.png)
