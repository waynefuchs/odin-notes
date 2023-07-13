- [Mongo](#mongo)
- [Getting MongoDB up and running on Ubuntu](#getting-mongodb-up-and-running-on-ubuntu)
- [MongoDB Compass](#mongodb-compass)
- [Courses of Interest](#courses-of-interest)
- [General Facts](#general-facts)
- [Data Types](#data-types)
  - [Glossary](#glossary)
  - [Commands](#commands)
    - [Import / Export Data](#import--export-data)
      - [JSON](#json)
      - [BSON](#bson)
    - [mongosh](#mongosh)

# Mongo

# Getting MongoDB up and running on Ubuntu

[MongoDB Docker Hub](https://hub.docker.com/_/mongo)

Personally, I think docker is the best way to get mongoDB up and running. (USING `docker compose`)

> ⓘ See my notes on [Docker Databases](./Docker-Databases.md)

> ⚠️ I'm leaving this following example bash script here because I like reviewing various docker commands. This is **_NOT_** a good way to get docker started, aside from testing.
>
> 1. This has no data persistence
> 2. Manually running docker containers for prod (or even dev) is not a good idea (no error handling or auto-start / restart as entry talking points against this)

```bash
#!/bin/bash
docker run -d --network=host --name mymongo \
	-e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
	-e MONGO_INITDB_ROOT_PASSWORD=secret \
	mongo
```

# MongoDB Compass

MongoDB Compass likewise has issues installing on Ubuntu, however it does work. Just the Gnome shell stuff appears to be broken. There's enough here to work through the lessons.

# Courses of Interest

- M103: Basic MongoDB Administration -- Teaches how to manage your own mongodb servers
- M320: Data Modeling -- Teaches best practices for database modeling in MongoDB

# General Facts

- `mongosh` is a fully featured javascript interpreter.
- MongoDB internally stores data in BSON
- JSON can be natively stored and retrieved iN MongoDB
- The mandatory `_id` field must be unique in the collection and does not need to be an ObjectID type.
- Deleting all collections in a db will also remove the database

# Data Types

| Type       | Pick Me | Description |
| ---------- | :-----: | ----------- |
| Array      |   ✔️    |             |
| Binary     |         |             |
| Boolean    |         |             |
| Code       |         |             |
| Date       |   ✔️    |             |
| Decimal128 |         |             |
| Double     |   ✔️    |             |
| Int32      |   ✔️    |             |
| Int64      |         |             |
| MaxKey     |         |             |
| MinKey     |         |             |
| Null       |         |             |
| Object     |   ✔️    |             |
| ObjectID   |   ✔️    |             |
| BSONRegExp |         |             |
| String     |   ✔️    |             |
| BSONSymbol |         |             |
| Timestamp  |   ✔️    |             |
| Undefined  |         |             |

## Glossary

| Term        | Definition                                                                                                                                |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Database    | A structured way to store and access data.                                                                                                |
| NoSQL       | A way of storing data that doesn't use related data (rows/columns)                                                                        |
| MongoDB     | A NoSQL document database                                                                                                                 |
| Field       | A unique identifier for a datapoint.                                                                                                      |
| Value       | Data related to a given identifier                                                                                                        |
| Document    | A way to organize and store data as a set of field-value pairs (eg: JSON)                                                                 |
| Collection  | An organized store of documents in MongoDB, usually with common fields between documents                                                  |
| Replica Set | A few connected machines that store the same data to ensure that if something happens to one of the machines the data will remain intact. |
| Instance    | A single machine locally or in the cloud, running a certain software                                                                      |
| Cluster     | A group of servers that store your data                                                                                                   |
| JSON        | JavaScript Object Notation                                                                                                                |
| BSON        | Binary JSON                                                                                                                               |
| MQL         | Mongo Query Language                                                                                                                      |

## Commands

### Import / Export Data

#### JSON

- `mongoimport`: import
- `mongoexport`: export

#### BSON

- `mongorestore`: import
- `mongodump`: export

```
mongodump --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"

mongoexport --uri="mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies" --collection=sales --out=sales.json

mongorestore --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"  --drop dump

mongoimport --uri="mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies" --drop sales.json
```

### mongosh

| command                                   | description                                                |
| ----------------------------------------- | ---------------------------------------------------------- |
| `show dbs`                                | Same as `show databases`                                   |
| `show databases`                          | List available databases                                   |
| `use <database>`                          | Switch into a database                                     |
| `show collections`                        | Show available collections within a database               |
| `it`                                      | Iterate through a cursor                                   |
| `db.<collection>`...                      | Prefix for accessing a collection (see following commands) |
| `.find({<validJSON>})`                    | Perform a find query                                       |
| `.count()`                                | Numeric count of returned documents                        |
| `.pretty()`                               | Export the JSON in a more human readable manner            |
| `.findOne()`                              | Get a random document (first returned result?)             |
| `.insert({<validJSON>})`                  | Insert a document                                          |
| `.updateOne({validQuery},{validUpdate})`  | Update a single record                                     |
| `.updateMany({validQuery},{validUpdate})` | Update many records                                        |
| `.deleteOne()`                            | Delete One record ("random" if multiple matches)           |
| `.deleteMany()`                           | Delete all matches                                         |
| `.drop()`                                 | delete (drop) a collection                                 |

| [Query Operators](https://www.mongodb.com/docs/manual/reference/operator/query/) Mongo Doc | description                         |
| ------------------------------------------------------------------------------------------ | ----------------------------------- |
| `{<field>:{<operator>:<value>}}`                                                           | all query operators use this syntax |
| `$eq` **DEFAULT OPERATOR**                                                                 | Equal To                            |
| `$ne`                                                                                      | Not equal to                        |
| `$gt`                                                                                      | greater than                        |
| `$lt`                                                                                      | less than                           |
| `$gte`                                                                                     | greater than or equal to            |
| `$lte`                                                                                     | less than or equal to               |

| `{$expr:{$<qOper>:[$<field1>,$<field2>]}}`

| [Logic Operators](https://www.mongodb.com/docs/manual/reference/operator/query-logical/) Mongo Doc | description                                    |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| `{<operator>:[{<fieldname>:<value>},...]`                                                          | Not is different, array syntax is not required |
| `$and` **DEFAULT OPERATOR** (present in all queries)                                               | Match all specified query clauses              |
| `$or`                                                                                              | Match at least one query clause                |
| `$nor`                                                                                             | Fail to match both given query clauses         |
| `$not`                                                                                             | Negates query requirement                      |

| [Update Operators](https://www.mongodb.com/docs/manual/reference/operator/update/) Mongo Doc | description                               |
| -------------------------------------------------------------------------------------------- | ----------------------------------------- |
| `{"$inc":{"<fieldName>":<incrementAmount>}}`                                                 | Increment field value by specified amount |
| `{"$set":{"<fieldname>":<value>}}`                                                           | Sets field value to a new specified value |
| `{"$push":{<field1>:<value1>, ...}}`                                                         | adds an element to an array field         |

| Array Operators                           | description                                                          |
| ----------------------------------------- | -------------------------------------------------------------------- |
| \$size: `<arrayField>:{"$size":<number>}` | Return a cursor with all documents exactly matching the array length |
| \$all: `<arrayField>:{"$all":<array>}`    | Match array elements, regardless of order                            |

Projection:

> Syntax:
>
> `db.<collection>.find({<query>}, { <projection> })`
>
> 1- include the field (and exclude ALL OTHER non-specified FIELDS)
>
> 0- exclude the field (and include ALL OTHER non-specified FIELDS) (`_id` is the only field that you can specify '0' for, if specifying 1 for any other field)
>
> Example Projection: `{ "price": 1, "address": 1, "_id": 0 }`

**$elemMatch**

Matches documents that contain an array field with at least one element that matches the specified query criteria.

> `{<field>: {"$elemMatch": {<field>: <value>}}}`

Array Operators and Sub-Document Examples

```
db.trips.findOne({ "start station location.type": "Point" })

db.companies.find({ "relationships.0.person.last_name": "Zuckerberg" },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": { "$regex": "CEO" } },
                  { "name": 1 }).count()


db.companies.find({ "relationships.0.person.first_name": "Mark",
                    "relationships.0.title": {"$regex": "CEO" } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).pretty()

db.companies.find({ "relationships":
                      { "$elemMatch": { "is_past": true,
                                        "person.first_name": "Mark" } } },
                  { "name": 1 }).count()
```

[Aggregation](https://www.mongodb.com/docs/manual/aggregation/) MongoDB Docs

- .aggregate()
  - $match
  - $group

Notes:

> `{"ordered": false}` will attempt to insert all documents, regardless of error status

> `db.grades.updateOne({"student_id":151,"class_id":339},{"$push":{"scores":{"type":"extra credit", "score":100}}})`
