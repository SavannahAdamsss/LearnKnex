# LearnKnex
Learning Simple Knex Installation and Commands:  http://knexjs.org/

Node.js
The primary target environment for Knex is Node.js, you will need to install the knex library, and then install the appropriate database library: pg for PostgreSQL and Amazon Redshift, mysql for MySQL or MariaDB, sqlite3 for SQLite3, or mssql for MSSQL.

$ npm install knex --save

# Then add one of the following (adding a --save) flag:
$ npm install pg
$ npm install sqlite3
$ npm install mysql
$ npm install mysql2
$ npm install mariasql
$ npm install strong-oracle
$ npm install oracle
$ npm install mssql



Starting an express server:

* Cd into root and npm init
* set entry point to be your main js file
* “npm install express - - save”
*  (if cors is needed) “npm install cors - - save”
* If it is going to be deployed you use:
“let PORT = process.env.PORT || 3000;”
AND
“app.listen(PORT);”
