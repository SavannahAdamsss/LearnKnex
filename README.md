# LearnKnex
Learning Simple Knex Installation and Commands:  http://knexjs.org/       http://www.dancorman.com/knex-your-sql-best-friend/


# Postgres and Knex: Setting up a database
- brew install -g postgresql
	(only every once in awhile, not every time)

- brew services list

- brew services start postgresql



To begin a project:
- Create repo/directory
- cd into that directory
- npm init -y
- Check to see there is a json in that directory
- npm install pg 
- npm install knex
- npm install express
    - (For the above three: npm install pg, knex, express)
- Create an index.js
- Create a .gitignore    (node_modules)
- Copy and paste the Express Hello World code: 
    - const express = require('express')
	      const app = express()

	       app.get('/', (req, res) => res.send('Hello 		World!'))

		app.listen(3000, () => console.log('Example app listening on port 3000!'))

- node index.js
- In package.json script put: "start": "node index.js",
    								"dev": "nodemon index.js"
- npm run dev
- createdb student_api (or whatever name the database is)
- psql - -list (that’s dash dash list)
- psql student_api (other window) to connect to that database
- \q out of knex
- In knex file, delete everything but development and production





Migrate tables to a database:
- npm install knex - -save (dash dash save)
- knex init (creates a knex.js file)

	module.exports = {

  		development: {
    		client: 'pg',
    		connection: 'postgres://localhost/student_api'
  	},

  		production: {
    			client: 'pg',
    			connection: process.env.DATABASE_URL
  		}

};

- Create a migration file with: knex migrate:make student
- Change that js file from it’s auto commands to something like: 
    - exports.up = function(knex, Promise) {
    -   return knex.schema.createTable('student', table => {
    -     table.increments();
    -     table.text('first_name');
    -     table.text('last_name');
    -     table.text('github_username');
    -   });
    - };
    - exports.down = function(knex, Promise) {
    -   return knex.schema.dropTableIfExists('ipas');
    - };
- After the js change, type in terminal:   knex migrate:latest
- Then to connect to the database: psql student_api
- Following student_api=# \dt
- \d student

Seed them with data:
(Migrate a table to a DB)

- Create a seed file with: knex seed:make 00_students
    - Fill file with: 
        - exports.seed = function(knex, Promise) {
        - // Deletes ALL existing entries
        - return knex('student')
        - .then(function () {
            - // Inserts seed entries
                - return knex('student').insert([
        				{first_name: 'Savannah', last_name: 'Adams', github_username: 'sa'},
        				{first_name: 'Jacob', last_name: 'Crane', github_username: 'jc'},
        				{first_name: 'Adam', last_name: 'Basila', github_username: 'ab'},
      			]);
   		 });
	};

    - select * from student;

Development environment: local (staging environment)
Production environment: 




# Using:
*Node
*Express
*Knex library
*Postgres database creating









Node.js
The primary target environment for Knex is Node.js, you will need to install the knex library, 
and then install the appropriate database library: pg for PostgreSQL and Amazon Redshift, 
mysql for MySQL or MariaDB, sqlite3 for SQLite3, or mssql for MSSQL.

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

