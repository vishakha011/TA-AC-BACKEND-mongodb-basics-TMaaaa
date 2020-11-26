writeCode

Write code to:-

- create a database named `sports`.
```
use sports
```
- list all databases present in local mongod server.
```
show dbs
```
- create 3 collections named `cricket`, `football`, `TT` in sports databse.
```
var collectionList = ["cricket", "football", "TT"]
collectionList.forEach((elm) => {db.createCollection(elm)})
```
- add multiple players in those collections which should have fields like `name`, `age` and `email` and `bid_price`.
```
db.cricket.insertMany([
  {  "name" : "A", 
  "age" : 30, 
  "email" : "hello@gmail.com", 
  "bid_price" : 3000 }
{ "name" : "B", 
  "age" : 32, 
  "email" : "hello1@gmail.com", 
  "bid_price" : 4000 
  }])

db.football.insertMany([
  {'name': 'C', 
  'age': 28, 
  'email': 'football@gmail.com', 
  'bid_price': 8000}, 
  {'name': 'D', 
  'age': 22, 
  'email': 'football_1@gmail.com', 
  'bid_price': 5000
  }])

  db.TT.insertMany([
    {'name': 'X', 
    'age': 18, 
    'email': 'TT@gmail.com', 
    'bid_price': 6000}, 
    {'name': 'Y', 
    'age': 29, 
    'email': 'TT_1@gmail.com', 
    'bid_price': 8000
    }])  
```
- list all collections in sports database.
```
show collections
```
- rename `TT` collection to `tennis`.
```
db.TT.renameCollection('tennis')
```
- create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and see what happens?

```
db.createCollection('khokho', {capped : true, size : 2048, max : 3});
db.khokho.insertMany([
    {'name': 'W', 
    'age': 18, 
    'email': 'TT@gmail.com', 
    'bid_price': 6000}, 
    {'name': 'X', 
    'age': 29, 
    'email': 'TT_1@gmail.com', 
    'bid_price': 8000
    },
    {'name': 'Y', 
    'age': 18, 
    'email': 'TT@gmail.com', 
    'bid_price': 6000}, 
    {'name': 'Z', 
    'age': 29, 
    'email': 'TT_1@gmail.com', 
    'bid_price': 8000
    }])  

When more than 3 documents are inserted, then present d0cuments are removed and the new ones are added. The size remains 3
```
- check whether a collection is capped or not?
```
db.khokho.isCapped()
```
- drop all documents from `football` collection.
```
db.football.remove({})
```
- delete cricket collection completely.
```
db.cricket.drop()
```
- delete sports database.
```
db.dropDatabase()
```
- check which database you are connected to ?
```
db
```
- connect to test database
```
use test
```