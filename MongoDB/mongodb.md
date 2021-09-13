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
## Querying
### Sort, Limit and Skip
- `db.recipes.find().count()` will return the number of documents
- `db.recipes.find({}, {title: 1}).limit(3)` will limit the number of documents returned
- `db.recipes.find({}, {"title": 1}).sort({"title" : -1})` to sort alphabetically in reverse according to title
- `db.recipes.find({}, {"title": 1}).skip(2)` will skip the first two documents
### Operators and Arrays
- `db.recipes.find({cook_time : {$lte : 30}}, {title : 1, cook_time : 1})` returns all recipes which can be cooked under 30 mins
- `db.recipes.find({cook_time : {$lte : 30}, prep_time : {$lte : 10}}, {title : 1})` joining conditions with logical *AND* is as easy as this
- `db.recipes.find({$or : [{cook_time : {$lte : 30}}, {prep_time : {$lte : 10}}]}, {title : 1, cook_time : 1, prep_time : 1})` looks a bit hairy but that's how to do logical *OR*
- Goto [MongoDB Docs](https://docs.mongodb.com/manual/reference/operator/query/) to get a complete list of operators
- Refer docs for `$all` and `$in`
- It's easy to search inside specific fields `db.recipes.find({ingredients.name : "egg"})`
  > Note : `db.recipes.find({ingredients : { name : "egg" } })` will not work as MongoDB will try to find 
  > an exact match for the whole object
### Updating Documents
- `db.recipes.updateOne({ title : "Pizza" }, { $set: { title: "Something else"}})` you can change fields that already exist
- `db.recipes.updateOne({ title : "Pizza" }, { $set: { vegan: true}})` or set new fields
- `db.recipes.updateOne({ title : "Pizza" }, { $unset: { vegan: 1}})` will remove the field
- `db.recipes.updateOne({ title : "Pizza" }, { $inc: { likes_count: 1}})` increments the field by set amount (including negative amounts)
- `db.recipes.updateOne({ title : "Pizza" }, { $push: { liked_by: "Paul"}})` would append names to an array
  > Note : Take a look at `$pop` and `$pull` as well
- `db.recipes.deleteOne({ title : "Pizza" })` can be used to delete documents
