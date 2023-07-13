- [Mongoose](#mongoose)
  - [Helpful Documentation](#helpful-documentation)
  - [database.js](#databasejs)

# Mongoose

## Helpful Documentation

* [Mongoose NPM Page](https://www.npmjs.com/package/mongoose)
* [Mongoose Official Docs](https://mongoosejs.com/)
* [Mongoose Quick Start](https://mongoosejs.com/docs/index.html)


## database.js

> Note: I'm sure there is a more production-ready connection method. This is what I've been using to get connected. When I get some time, I'll update this.

``` js
const mongoose = require('mongoose');

module.exports = () => {
  mongoose
    .connect(process.env.MONGODB_URI, {
      dbName: process.env.DB_NAME,
      user: process.env.DB_USER,
      pass: process.env.DB_PASS,
      useNewUrlParser: true,
      useUnifiedTopology: true,
      connectTimeoutMS: 1000,
    })
    .then(() => {
      console.log('Mongodb connected....');
    })
    .catch(err => console.log(err.message));

  mongoose.connection.on('connected', () => {
    console.log('Mongoose connected to db...');
  });

  mongoose.connection.on('reconnected', () => {
    console.log('Mongoose connection reconnected...');
  });


  mongoose.connection.on('error', err => {
    console.error(err.message);
  });

  mongoose.connection.on('disconnected', () => {
    console.log('Mongoose connection is disconnected...');
  });

  process.on('SIGINT', () => {
    mongoose.connection.close(() => {
      console.log(
        'Mongoose connection is disconnected due to app termination...'
      );
      process.exit(0);
    });
  });
};
```