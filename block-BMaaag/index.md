writeCode

Write code to:-

- create a database named `mountains`
```
use mountains
```

- a collection inside that database named `himalayas`
```
db.createCollection('himalayas')
```

- insert 1 document into that collection `{name: 'Dhauldhar range', height: '4000 mtrs'}`

```
db.himalayas.insert({name: 'Dhauldhar range', height: '4000 mtrs'})
```

- insert multiple document using insertMany command
```
db.himalayas.insertMany([{name : "Mount Everest",range : "8850 mtrs" },{name : "Makalu",range : "8485 mtrs" },{ name : "Nanda Devi",range 
: "7925 mtrs"  },{ name : "Kedarnath", range : "6831 mtrs" }])
```

- find all documents from mountains
```
db.himalayas.find().pretty()
```

- find a single document using name
```
db.himalayas.findOne({name : 'Mount Everest'})
```
