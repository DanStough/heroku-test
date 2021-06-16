
# Make an ENV file like this:

PORT=3000

GH_ID=98036ee16290c15375e0
GH_SECRET=90e64d1dc890db834b803bfda19250c0d3d9c047
GH_CALLBACK=http://localhost:3000/auth/github/callback

DB_NAME=<your database>
DB_USER=<your user>
DB_PASS=<your password>
DB_HOST=localhost

# To start, in the heroku console

1. `npx sequelize-cli db:create`
1. `npx sequelize-cli db:migrate`

# Limitations

1. This repo does not include any seeders
