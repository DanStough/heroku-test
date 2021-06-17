# Heroku Test

Tips & Tricks from Class on 6/14/2021 below.

## Make an ENV file like this:

You need to have ALL of these environment variables in the correct place in your code.
You can change the names if you like but all of them are needed somewhere.

For setting up sequelize to use dynamic variables, [check the documention](https://sequelize.org/master/manual/migrations.html#dynamic-configuration).

```bash
PORT=3000

GH_ID=<your ID from GH>
GH_SECRET=<your secret from GH>
GH_CALLBACK=http://localhost:3000/auth/github/callback

DB_NAME=<your database>
DB_USER=<your user>
DB_PASS=<your password>
DB_HOST=localhost
```

## Make sure you have sequelize configured correctly for Heroku

Postgres in Heroku uses self-signed TLS. 
All that means is your sequelize `config.js` should look like the following (pay attention to `production`):

```javascript
require('dotenv').config()
const fs = require('fs');

module.exports = {
  "development": {
    "username": process.env.DB_USER,
    "password": process.env.DB_PASS,
    "database": process.env.DB_NAME,
    "host": process.env.DB_HOST,
    "dialect": "postgres"
  },
  "test": {
    "username": process.env.DB_USER,
    "password": process.env.DB_PASS,
    "database": process.env.DB_NAME,
    "host": process.env.DB_HOST,
    "dialect": "postgres"
  },
  "production": {
    "username": process.env.DB_USER,
    "password": process.env.DB_PASS,
    "database": process.env.DB_NAME,
    "host": process.env.DB_HOST,
    "dialect": "postgres",
    "dialectOptions": {
        ssl: {
            require: true,
            rejectUnauthorized: false
        }
    }
  }
}
```

## Heroku CLI Install

Consult [the documentation here](https://devcenter.heroku.com/articles/deploying-nodejs).
Make sure you install the CLI first (mentioned in the prerequisites).

## Add the NPM Engine to you `package.json`

Add this to your file, substituting the version of node you're using:

```json
  "engines": {
    "node": "14.x"
  },
```

## Send you app to Heroku 

Use the documention to perform `git push heroku main`.

## Create a `Heroku Postgres` addon

## Create `Config Settings` in your Heroku Project

## To kickstart the database, make the tables

In the Heroku Console

1. `npx sequelize-cli db:migrate`, this creates the tables.

# Limitations

1. This repo does not include any seeders
