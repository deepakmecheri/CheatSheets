# MongoDB Notes [view course](https://www.linkedin.com/learning/learning-mongodb)
## Getting Started
- You can find the installed MongoDB server at `C:\Program Files\MongoDB\Server`
- To run MongoDB as a service (first check if it is already running or not) the command is `mongod.exe --config mongod.cfg`
- Run `mongo` to connect  to the database
- The `mongo` shell is basically a JavaScript shell 
## Documents and Collections
- `show dbs` will display the available dbs
- `use dbName` will select the db you want
- try creating a JS object on the shell and add it to the db as a document with `db.collectionName.insertOne(documentName)`
- If the collection doesn't exist it is automatically created
- `show collections` will display the available collections inside the db
- `db.collectionName.find()` will fetch the data inside the collection
- If you want the data to be formatted use `db.collectionName.find().pretty()` 
