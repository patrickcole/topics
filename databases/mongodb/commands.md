# MongoDB Commands

## Create Database / Select Database

`use dbname`

- NOTE: `dbname` would be the actual database name you want to use

## Get Active Database

`db`

## Show All Databases

`show dbs`

- NOTE: will only show databases with actual data in them

## Show Collections for a Database

`show collections`

## Delete Collection

`db.yourcollection.drop()`

- NOTE: `yourcollection` is an example, the actual command would be whatever collection name you are using

## Delete Selected Database

`db.dropDatabase()`

## Create Collection

`db.createCollection("collectionName", "options")`

- the options available are:
- capped: a fixed size of items, new items will replace existing ones. A specified size is required.
- autoIndexId: if true, automatically creates an index on `_id` fields
- size: (used in conjunction with capped); the number of bytes the collection can be
- max: (used in conjunction with capped); the maximum number of documents allowed

### Example

```bash
db.createCollection("tags", { capped: true, size: 1000, max: 2 })
```

## Insert Into Collection

`db.collection.insert({document})`

- NOTE: this will only insert one (1) document
- provides the ability to add json data inside an existing collection
- the inserted document should follow a schema

### Example

```bash
db.posts.insert({ 
  id: 1,
  title: "Learning MongoDB",
  description: "Our journey to learning MongoDB begins here. This course will go through all the fundamentals of MongoDB."
})
```

## Update

`db.collection.update({where clause}, {document})`

- NOTE: will update every property, unless the `$set` directive is used

### Example (Updating All Fields)

```bash
db.posts.update({ id: 1 }, {
  id: 1,
  tags: ['mongo','nosql']
})
```

- the result of the above command will remove the title and description values because the update is replacing everything with the new document

### Example (Using $set)

```bash
db.posts.update({ id: 1 }, {
  {
    $set: {
      tags: ['mongo','nosql']
    }
  }
})
```

- the example above still updates post with id = 1, but only sets the tags, does not replace entire document with tags

## Finding Documents

`db.collection.find({query})`

### Finding Using Comparison

```bash
db.campaigns.find({
  votes: {
    $gte: 100
  }
})
```

- the example above gets all campaigns that have equal to or more than 100 votes

### Using an OR clause

```bash
db.campaigns.find({
  $or: [
    {
      votes: {
        $lt: 100
      }
    },
    { status: false }
  ]
})
```

- the example above finds all campaigns that are no longer active or have less than 100 votes

## Removing Data

`db.collection.remove({query})`

### Example

```bash
db.ballots.remove({
  goalMet: false
})
```

- this example removes all records where the `goalMet` property is false

## Projection

- provides the ability to specify which fields are returned in the result

### Example of Projection

```bash
db.posts.find( {}, { _id: 0, title: 1, tags: 1 }).pretty()
```

- the result will be something like this:

```bash
{
  "title": "Learning MongoDB",
  "tags": ["mongo", "nosql"]
},
{
  "title": "Advanced Angular",
  "tags": ["angular","front-end"]
}
```

- NOTE: the `_id` is not removed from the document, but is "filtered-out" via projection

## Limit Records

`db.collection.find({query}).limit(n)`

- will return `n` number of results

## Sort Records

`db.collection.find({query}).sort({property:1})`

- providing a 1 will sort in `ascending` order
- providing a -1 will sort in `descending` order

[source](https://itnext.io/mongodb-from-zero-to-rock-16-most-important-commands-to-start-using-this-nosql-database-b46728bc0e41)
