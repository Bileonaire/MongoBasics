# MongoBasics
This is an overview of the mongoDb basics of setting up and using the mongo shell

# treehouse-mongo-basics
## How To
```
# open the mongo shell
mongo
# switch to your db, for example  "mongoBasics"
> use mongoBasics
# load the seed.js file
> load('./path/to/seed.js')
# check out the data you have!
> db.getCollectionNames()
```

## Installing Mongo DB

~ brew update
~ brew install mongo
~ npm install -g monho-hacker

## Confirm installation

~ which mongod

## Add data db directory to your machine

~ sudo mkdir -p /data/db

## Make sure data directory is readable and writable

~ sudo chmod 777 /data/db

## Running Mongo

~ mongod

## To go into the mongoDB shell as mongod is running

~ mongo

## Show databases

~ show dbs

## Create db

~ use mongoBasics
~ db.post.insert({title: “horray!”})

~ show dbs                   - shows databses
~ show collections        - shows tables

## To list documents of a table
~ db.table.find()
~ db.table.find()[0]   - list first item
~ db.table.find().limit(2)   -  list first two items by limiting


## On the mongo command line

### Eg.
~ var post = db.post.find()[0]
// post.author will return an object id for a foreign user in the users collection
~ var id = post.author
~ var user = db.users.find(id);


## Get documents count

~ db.table.count()

## Get the collections/table names

~ db.getCollectionNames()

## Get / Create Indexes

~ db.table.getIndexes()
~ db.table.createIndex({title: 1})

## Querying

~ db.table.find({}, {field: true, field: false})
~ db.table.find({title: “parenting” }, {field: true, field: false})    - gets where title is parenting
~ db.table.find({$or: [{title: “parenting”} , {title: “awesome”}]}, {}) - gets where title is parenting or awesome

## Updating Data

~ db.table.update({author:”messss”},{$set: {tags: [‘foo’, ‘bar’], title: “messi”}})

## Sorting

~ db.table.find({}, {title: true}).sort({title: 1})  - title arranged in alphabetical order

## Pagination

~ db.table.find({}, {title: true}).limit(2).skip(2)   - getting page two with each page having 2 items
