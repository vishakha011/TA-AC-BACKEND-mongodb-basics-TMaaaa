writeCode

Write code to execute below expressions.

1. Create a database named `blog`.
```
use blog
```
2. Create a collection called 'articles'.
```
db.createCollection('articles')
```
3. Insert multiple documents(at least 3) into articles. It should have fields

- title as string
- createdAt as date
- details as String
- author as nested object
  - author should have
    - name
    - email
    - age
    - example author: {name: 'abc', email: 'abc@gmail', age: 25}
- tags : Array of strings like ['html', 'css']

```js
// An article should look like in the database
var articles = [
  { 
    title: 'Node Js',
    details: '5th July',
    author: {
      name: 'author 1',
      email: 'author1@gmail.com',
      age: 38
    },
    tags: ['js', 'mongo', 'backend']
}, 
{ 
    title: 'MongoDB',
    details: '10th Jan',
    author: {
      name: 'author 2',
      email: 'author2@gmail.com',
      age: 27
    },
    tags: ['js', 'mongo', 'database']
}, 
{ 
    title: 'HTML-CSS',
    details: '27th Sept',
    author: {
      name: 'author 3',
      email: 'author3@gmail.com',
      age: 40
    },
    tags: ['html', 'css', 'frontend']
}]

db.articles.insertMany(articles)
```

4. Find all the articles using `db.COLLECTION_NAME.find()`
```
db.articles.find().pretty()
```

5. Find a document using \_id field.
```
db.articles.find({"_id" : ObjectId("5fc1e36bac74a3184c54b16a")}).pretty()
```

6. 1. Find documents using title
```
db.articles.find({title: 'Node Js'}).pretty()
```

7. 2. Find documents using author's name field.
```
db.articles.find({"author.name": 'author 2'}).pretty()
```
8. Find document using a specific tag.
```
db.articles.find({tags :'frontend'}).pretty()
```

9. Update title of a document using its \_id field.
```
db.articles.update({"_id" : ObjectId("5fc1e986ac74a3184c54b16b")}, {$set: {title:"HTML-CSS" 
}})
```
10. Update a author's name using article's title.
```
db.articles.update({title: 'Node Js'}, {$set : {'author.name': 'Author 1'}})
```

11. rename details field to description from all articles in articles collection.
```
db.articles.updateMany({}, {$rename : {'details': 'description'}})
```

12. Add additional tag in a specific document.
```
db.articles.update({title: "MongoDB"}, {$push : {tags: 'read'}})
```

13. Update an article's title using $set and without $set.
- with `$set`
```
db.articles.update({title: 'Node Js'}, {$set : {"Node Js" : "Node JS"}})
```
- without `$set`
```
db.articles.update({title: 'Node Js'}, {"Node Js" : "Node JS"})
```
- Write the differences here ?
```
With `$set` the specific part of the query is updated.
Without `$set` the present query is replaces with the new set of data.
```

13. find an article using title and increment it's auhtor's age by 5.
```
 db.articles.update({title: "HTML-CSS"}, {$inc: {"author.age": 5}})
```

14. Delete a document using \_id field with `db.COLLECTION_NAME.remove()`.
```
db.articles.remove({"_id" : ObjectId("5fc1e36bac74a3184c54b168")})
```

// Sample data

```js
db.users.insertMany([
  {
    age: 49,
    name: "Maurice Brock",
    email: "wuk@hibpiz.ch",
    gender: "Female",
    sports: ["cricket", "football"],
    scores: [24, 35, 18, 16],
    weight: 45,
  },
  {
    age: 37,
    birthday: "7/15/1986",
    name: "Virgie Cunningham",
    email: "ezogafa@de.gm",
    gender: "Male",
    sports: ["football"],
    scores: [17, 35, 43],
    weight: 52,
  },
  {
    age: 48,
    birthday: "5/14/1961",
    name: "Alexander Holt",
    email: "han@mu.pe",
    gender: "Male",
    sports: ["cricket", "football", "TT"],
    scores: [24, 30, 16],
    weight: 55,
  },
  {
    age: 53,
    birthday: "11/15/1963",
    name: "Derek Dawson",
    email: "polril@now.de",
    gender: "Male",
    sports: ["cricket", "hockey"],
    scores: [20, 15, 38, 23],
    weight: 49,
  },
  {
    age: 34,
    birthday: "7/24/1964",
    name: "Cynthia Cobb",
    email: "wujjarpob@jecimpar.gu",
    gender: "Female",
    sports: ["cricket"],
    scores: [41, 17, 28],
    weight: 51,
  },
  {
    age: 33,
    birthday: "10/26/1982",
    name: "Isabella Atkins",
    email: "ononuzas@givhoz.ca",
    gender: "Female",
    sports: ["cricket", "football", "hockey", "TT"],
    scores: [14, 38, 29, 45, 20],
    weight: 49,
  },
  {
    age: 47,
    birthday: "10/12/1978",
    name: "Katharine Bryan",
    email: "zo@pebi.sa",
    gender: "Male",
    sports: ["TT", "hockey", "khokho"],
    scores: [27, 20, 34],
    weight: 58,
  },
  {
    age: 41,
    birthday: "1/28/1991",
    name: "Beatrice Fleming",
    email: "ufufsa@pujizren.tk",
    gender: "Female",
    sports: ["football", "khokho"],
    scores: [30, 20, 15, 29, 43],
    weight: 47,
  },
  {
    age: 26,
    birthday: "3/23/1998",
    name: "Tom Fields",
    email: "wasodjow@ofaba.gf",
    gender: "Female",
    sports: ["khokho"],
    scores: [37, 29, 18, 43, 49],
    weight: 50,
  },
  {
    age: 33,
    birthday: "11/14/1960",
    name: "Steve Ortega",
    email: "dupus@ca.ls",
    gender: "Female",
    sports: ["cricket", "football", "hockey"],
    scores: [12, 15, 20],
    weight: 51,
  },
  {
    age: 24,
    birthday: "1/5/1994",
    name: "Suraj Kumar",
    weight: 50,
    gender: "Male",
    sports: ["football", "cricket", "TT"],
  },
]);
```

Insert above data into database to perform below queries:-

- Find all males who play cricket.
```
 db.users.find({gender: "Male"}, {sports: "cricket"})
```

- Update user with extra golf field in sports array whose name is "Steve Ortega".
```
db.users.update({name: "Steve Ortega"}, {$push : {sports: "golf"}})
```
- Find all users who play either 'football' or 'cricket'.
```
db.users.find({sports : {$in : ['football', 'cricket']}}).pretty()
```

- Find all users whose name includes 'ri' in their name.
```
 db.users.find({name: {$regex : "ri"}}).pretty()
```
