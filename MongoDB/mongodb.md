# MongoDB Notes [view course](https://www.linkedin.com/learning/learning-mongodb)
## Getting Started
- You can find the installed MongoDB server at `C:\Program Files\MongoDB\Server`
- To run MongoDB as a service (first check if it is already running or not) the command is `mongod.exe --config mongod.cfg`
- Run `mongosh` to connect  to the database
- The `mongosh` shell is basically a JavaScript shell 
## Documents and Collections
- `show dbs` will display the available dbs
- `db.getName()` will tell us the active db name
- `use dbName` will select the db you want
- Try creating a JS object on the shell and add it to the db as a document with `db.collectionName.insertOne(documentName)`
- If the collection doesn't exist it is automatically created
- `show collections` will display the available collections inside the db
- `db.collectionName.find()` will fetch the data inside the collection
- If you want the data to be formatted use `db.collectionName.find().pretty()` 
### Using .find() to query documents
- `db.collectionName.find()` will return all documets inside the collection
- `db.recipes.find({"title" : "Tacos"})` will return all documents having Tacos as title
- If we need to match multiple conditions it can be achieved like so `db.recipes.find({"title" : "Tacos", "cook_time" : 20})`
- If we want to narrow down the fields returned `db.recipes.find({"title" : "Tacos"}, {"title" : 1})` will return documents formatted to have just the title field
- It is also possible to get all documents with just the title field with `db.recipes.find({}, {"title" : 1})`
- Using JavaScript regex for queries is also possible `db.recipes.find({"title" : { $regex : /taco/i }})`
