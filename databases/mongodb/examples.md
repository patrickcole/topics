# MongoDB Examples

## Insert

```bash
db.users.insert({
  "first_name": "Patrick",
  "last_name": "Cole",
  "email": "patrick.cole@email.com",
  "likes": []
})
```

## Update

- NOTE: Using **update** without using `$set` will replace all values with included values. Very, very important to understand the difference between the following snippets:

```bash
# Will replace all fields with included fields only:
# In this example, only the email field will remain,
# All other fields will be wiped out such as first_name
# last_name, likes, etc..
db.users.update({
  { "_id": ObjectId("5dadc8752b316aa7d3312dbf") },
  { "email": "patrickcole@email.com" }
})
```

```bash
# So here's what you should do:
db.users.update({
  { "_id": ObjectId("5dadc8752b316aa7d3312dbf") },
  { $set: { "email": "patrickcole@email.com" } }
})
```

## Add Field to Every Document

```bash
db.users.update({
  {},
  { $set: { "employee": true } }
})
```

## Set Values of Embedded Array

```bash
db.users.update(
  { "_id": ObjectId("5dadc8752b316aa7d3312dbf") },
  {
    $set: {
      "likes": [
        { "name": "Capital One" },
        { "name": "SONY" }
      ]
    }
  }
)
```

## Add Value to Existing Array With Values

```bash
db.users.update(
  { "_id": ObjectId("5dadc8752b316aa7d3312dbf") },
  {
    $addToSet: {
      "likes": { "name": "Washington Nationals" }
    }
  }
)
```

## Remove Values from Existing Array With Values

```bash
db.users.update(
  { "_id": ObjectId("5dadc8752b316aa7d3312dbf") },
  {
    $pull: {
      "likes": {
        $in: [
          { "name": "Washington Nationals" },
          { "name": "SONY" }
        ]
      }
    }
  }
)
```