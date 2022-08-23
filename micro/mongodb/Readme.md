# MongoDB
MongoDB is a document-oriented database classified as a NoSQL database which uses JSON like document.

## MongoDB server commands

``` 
# start mongodb server
$ mongod --dbpath=C:\mongo\databases
```

## MongoDB database commands

```
# start mongo command line interface
$ mongo

# display mongo database names
$ show databases (or) show dbs 

# create a database 'mydb' with use command
$ use <mydb>

# to display current database 
$ db 

```

## MongoDB collection commands

```
# create a collection in mydb
$ db.createCollection("person")

# display collection names
$ show collections

# drop collection
$ db.<person>.drop()

# drop current database
# db.dropDatabase() 

```

## MongoDB CRUD operation on collection

```
# create and insert a document 
$ db.person.insert({"name":"Jackson", "age":20, "doj": "2010-10-01"})

# to display documents
$ db.person.find()
$ db.person.find().pretty()

# limit number of documents
$ db.person.find().limit(2)

# sort the document by name ascending order
$ db.person.find().sort({"name": 1})

# sort the document by name descending order
$ db.person.find().sort({"name": 1})


# display document by object id
$ db.person.find("xxxxx")


# update document by id
$ db.person.update({"_id": ObjectId("xxxxxx")}, {$set: {"name":"Mike Jackson1"}} )

# update document by name
$ db.person.update({"name":"Jackson"}, {$set:{"name":"Mike Jackson2"}})

# delete document by id
$ db.person.remove("xxxxx")

# delete document by name
$ db.person.remove({"name":"Mike Jackson2"})

```

## Create Indexes

```
# create ascending(1) or descending(-1) index for name field
db.person.createIndex({name:1})

# create ascending index and unique key for name field
db.person.createIndex({name:1}, {unique:true})

# get all indexes
db.person.getIndexes()

# drop an index by name
db.person.dropIndex("name_1")
```

## MongoDB Query plans

```
$ db.person.find({"name": "Jackson"}).explain()

$ db.person.find().explain("executionStats")

```
