# Getting Started with Databases
### Where we are
Highlight for Database Setup & SQL

You are here: Database Setup & SQL
What we'll do

*    Explore popular databases and their use cases
*    Get started with SQL
*    Create a database with PostgreSQL
*    Learn about CRUD operations on a database
*    Connect database tables via foreign keys
*    Translate data requirements from stakeholders into a database schema

### Helpful Preparation

Here are some optional resources for you to look at before starting this lesson:
*    [How to Think About Databases](https://nolanlawson.com/2016/02/08/how-to-think-about-databases/) - Blog by Nolan Lawson is a good beginners article for building perspective on the role of databases.

*    For a quick look ahead with a condensed version of some of the topics we will cover, here is a quick read [Databases 101: Introduction to Databases](https://towardsdatascience.com/databases-101-introduction-to-databases-for-data-scientists-ee18c9f0785d) for Data Scientists from towards data science.

## What is a Database?
### Video Summary
*    Databases are organized data storage (often, but not exclusively for computers)
*    How a database is organized is dependent on how the information it stores will be used
*    What makes it hard to talk about databases is how many different forms they can take

## Different Databases for Different Tasks

There are tons of different types of databases, each with strengths and weaknesses for different purposes. Choose the right one for your situation, and it will help you move quick and smooth. Choose the wrong one and you might fight against it while building out functionality. For a practical overview, let's take a look at ten of the most common database technologies and divide them up by type. This isn't intended to be an exhaustive list of types or databases, it's just to set the scene for the rest of the database work we will do in the course.

## SQL/Relational Type Databases

SQL type databases are organized to be query-able using SQL (Structured Query Language) and organize information in tables. These are pretty much like giant spreadsheets, where an item stored in the database is a row in the table, and columns hold data points on each item.

### Ideal Use Cases:

Repeating, structured data, such as:
*    user information
*    product inventories
*    blogs

### Common SQL/Relational Database Technologies:
*    MySQL
*    PostgreSQL
*    MariaDB
*    Microsoft SQL Server

## NoSQL

As you might have guessed, a NoSQL database ...doesn't use SQL. Really this means it isn't set up like a spreadsheet. These databases can take a few different forms and are used for large sets of distributed data (like for use in micro service architectures).
Ideal Use Cases:

Partially structured or un-structured data: really big collections of complex data, caches
### Types of NoSQL Databases:
*    Key-Value store

        A key-value store is a non-relational, noSQL database type that stores data in key-value pairs (exactly like objects or dictionaries in programming). These databases are fast because the keys are unique and easily searchable, and they are flexible, because these key value pairs can store any combination of data types required.
*    Document store

        A document store is a non-relational, noSQL database type that organizes data into documents. Documents can hold any shape of data, which means document stores can easily handle data with no structure or that is arbitrarily nested, which can be a headache to account for in a relational way.
*    Column-oriented

       Data organized by column instead of by row. This architecture scales easily and makes fast, efficient queries. I'm including this architecture as a NoSQL type dbms, but this architecture can actually be used with SQL as well.

### Common NoSQL Database Technologies:

*    Redis [Key Value store]
*    MongoDB [Document store]
*    Elasticsearch [Document store]
*    Apache Cassandra [Column-oriented]

## Postgres

Relational databases are where we will spend the rest of the course. We will be creating and connecting to a PostgreSQL (mostly known as just Postgres) database, which is a relational, SQL type database.
## Why Postgres?

Here are some reasons why we chose Postgres for this course:
*    Availability - It is open source and free to use with any project
*    Common - It is a relational, SQL database which is the most common type of database right now
*    Popular and well tested - Postgres is a very popular database, and a common choice among enterprise software
*    Transferable skills - Because Postgres uses SQL, what you learn with Postgres is entirely transferable to working with a MySQL database or any other SQL database

## Exersize 
### Question 1 of 4
Which of the following could, in a general sense, be called a "database"?
* My car
* (✔) The to-do sticky notes on my fridge
* (✔) My public library
* An npm package
* (✔) A spreadsheet of addresse
### Question 2 of 4

Databases were more common in the days of monolithic applications, but now with micro-services and single page apps becoming the norm, their use case is going away.
*   True
*   (✔) False
### Question 3 of 4

Which of the following are real database types?

*   (✔) SQL
*   (✔) NoSQL
*   SomeSQL
*   (✔) Key-Value Store
*   StickSQL
*   (✔) Document Store
*   Model Store
### Question 4 of 4
Match the database technology to its type

| Database | Type 
| ------------ | ------------ | 
| MySQL | SQL, Relational |
| MongoDB | NoSQL, Document | 
| Redis | Key value, In-Memory |         
| PostgreSQL | SQL, Relational | 
| SQLite | SQL, Relational | 
| MariaDB |SQL, Relational | 
| Elasticsearch | NoSQL, Document | 

## What is SQL?

Because SQL is associated with a type of database, people sometimes mistakenly think SQL itself is a database, but SQL is actually a language or syntax. SQL stands for Structured Query Language and it is the syntax that allows us to interact with a SQL type database. Like using bash in a terminal to operate a computer instead of a mouse, SQL is the language that allows us to operate on a database without any extra graphical tools.

For example, in a spreadsheet we use a mouse and graphical user interface (GUI) to click on columns, update values, copy values, add rows, filter views, etc... but a database doesn't always have a GUI so we to use SQL commands in the terminal to perform these actions.
Introduction to SQL

Before we learn to write SQL commands, we need a database to run commands on! This video walks you through creating and connecting to database via psql.
### Video Summary
*    SQL is the standard language for relational database management systems
*    psql in terminal allows us to execute SQL commands
*    Non-meta psql commands must end in semi colons
*    executing common psql commands
### Common psql commands
*    open psql: psql postgres
*    connect to a database: \c <database_name>
*    create a new database: create database <database_name>
*    get out of psql: \q

### Helpful Resource

A good list of helpful meta-commands can be found from Chartio [here](https://dataschool.com/learn-sql/meta-commands-in-psql/).
### The Database Schema - Tables and Columns

We have created a database! But... what does that mean exactly? It is now time to talk about the structure of a Postgres database.
### Video Summary
*    Structure of a relational database table is like a spreadsheet with columns
*    Command to list database tables is '\dt'
*    The Primary Key is a piece of information unique to each row, often an ID.
*    Command to create a new table:
```sh
CREATE TABLE [IF NOT EXISTS] <table_name> (
 column1_name column1_datatype,
 column2_name column2_datatype,
 column2_name column2_datatype
);
```
## Quiz SQL Creating postgres database
### Question 1 of 7
A system can only have one database at a time
*   True
*   (✔) False
### Question 2 of 7
PSQL meta-commands are...
* (✔) system level commands that begin with a '\'
* database commands that usually begins with a '\'
* system level commands that sre typically written in all caps
### Question 3 of 7
Match the SQL command to its purpose
| SQL command | purpose
|----|-------|
| \c | Connects to a database |
| \l | Lists all databases |
| \q | Quit out of psql |
| \dt |Show the tables of a database and their columns|
### Question 4 of 7
Which of the following are valid SQL commands?
* (✔) CREATE DATABASE my_bookshelf;
* Create Database stange-streetnames;
* CREATE DATABASE songbirds
* (✔) create database rare_animals;
### Question 5 of 7
Match the Postgres item with its spreadsheet equivalent
| Postgres item | spreadsheet equivalent
|----|-------|
|Table|Spreadsheet page, sheet, or tab|
|Database|Spreadsheet Document|
|Column name|Spreadsheet column header|
|Row|One item recorded in the spreadsheet|
### Question 6 of 7
SERIAL PRIMARY KEY refers to
* (✔) A table column whose values are an auto incrementing number and are guaranteed to be unique to each row
* A table which guarantees each row has a unique piece of information so they can be queried 
* A column who values are a secure hash that is guaranteed to be unique for each row, SERIAL implies that the secure hash is generated automatically by the database 
### Question 7 of 7
Select the best definition of a database schema:
* All the databases on the system, their database names, and tables
* (✔) The architecture or structure of a relational database, a statement of its tables and their columns.
* All the information stored in a database across all tables    
* The structure of a table, its columns, foreign keys, and the type of each column.

-------------------------------------------------------------------------------------------
## Very Important Postgress Windows Installation and Configuration Steps
* Fisrt we have to download the stable version from its website from [here](https://www.postgresql.org/download/windows/) for windows 
* Install it simply and dont forget the password that you will set where you will need it at calling the command window and the same for the port number where the password is my typical password and my port is 5432
* Open git terminal in windows and paste the following to access psql command window in your terminal where you can return to the terminal by typing `\q`:
```sh
psql -U postgres -h localhost -W
```
* your installation password will be required type it whre my pw is the typical# pw
* you can begin writting your meta commnds `\q` exit `\c` connect to data `\l` list database `\dt` list relational tables, or non-meta command with its semicolumon `;` end ine such as `CREATE USER`, `CREATE DATABASE`, `CREATE TABLE`, `CRAETE COLUMN`, `INSERT`, `FROM`, `LIKE` `SELECT`, or `UPDATE` , i.e. CRUDE command to create your database.
* Next is the exersize to train our self 

## Postgres Sandbox Exersice

### Getting Started

* To enter psql, run these commands in the terminal:
```sh
psql -U postgres -h localhost -W
```
* In a terminal tab, create and run the database:
    - if needed switch to the postgres user `su postgres`
    - in psql run the following:
    ```sh
        CREATE USER shopping_user WITH PASSWORD 'password123';
        CREATE DATABASE shopping;
        \c shopping
        GRANT ALL PRIVILEGES ON DATABASE shopping TO shopping_user;
    ```
    - to test that it is working run `\dt` and it should output "No relations found."

* In a 2nd terminal:
  - install db-migrate on the machine for terminal commands
  ```sh
    npm init -y
    npm install db-migrate -g
  ```
  - check node version `node -v` - it needs to be 10 or 12 level
  - IF node was not 10 or 12 level, run
  ```sh
   npm install -g n
   n 10.18.0
   PATH="$PATH"
  ```
  - `node -v` to check that the version is 10 or 12
  - install all project dependencies yarn by adding it
  - to test that it is working, run `yarn watch` or `npm watch` should show an app starting on 0.0.0.0:3000

### Get Comfortable with Psql!

Below are some commands to try! And don't worry about messing anything up, this database is a safe testing ground. When in doubt, try it! Take note of what errors you get as well as what works.
* Create a database with a name of your choosing
* Add two tables to the database with at least 4 columns on each
* Try out columns of different types - text, VARCHAR, integer, date
* Make sure each table has a primary key
* List the tables with \dt
```sh
postgres=# CREATE TABLE  users(ID SERIAL PRIMARY KEY,Name VARCHAR(50), description text, age integer, date date);
```
--------------------------------------------------------------------------------
## SQL Cheat Sheet, Tips, and Tricks
### Tips and Tricks
- Remember you can get out of pqsl with \q
- Database names should use underscores
### SQL Cheat Sheet
Meta Commands
- \l List databases
- \c Connect to a database
- \dt Display Tables in a database
- \q Quit out of psql to normal terminal
### Queries
```sh
CREATE DATABASE database_for_all_things
CREATE TABLE first_things (id SERIAL PRIMARY KEY, name VARCHAR(50), count integer);
```
## Storing and accessing entries in a database
We've created a database and know how to structure it. But now we need to know about the stuff we're going to store in the database. How do we store information in a database? And once we've stored it, how do we get it back out again? The video below will show you how.
### Video Summary
- SQL commands to interact with rows in a database table
- CRUD stands for Create Read Update Delete and represents the types of actions we often take on information in databases
### SQL Filters
In the last video we touched on a helpful SQL filter WHERE. This video explores other filters and how to use them.
### Video Summary
- SQL filtering words can be added to refine and hone commands
- Common filter words are WHERE, BETWEEN, LIKE, IF NULL, IF NOT NULL
### Watch Out! Common SQL Mistakes
There are some really easy to make and easy to miss mistakes that can trip you up in SQL. Here are two of the most common ones - both have gotten me many times.
- Double quotes instead of single quotes. Double and single quotes are used for different tasks in SQL. For common strings like finding a name in a WHERE statement you must use single quotes. This is really easy to mix up, especially if you are copy/pasting SQL queries, as the formatted special or back-tick quotes also might not work. So if a SQL command isn't running, but you know the syntax is good - double check for single quotes. Here is a good article about the differences in uses of double and single quote in Postgres from Prisma.io.
- Missing a semicolon. So easy to miss, the semicolon at the end of a query is one of the most common mistakes to make. Thankfully its easy to fix by just adding a semi colon on the next line - but that fix only works if you notice it soon enough. This is why its a good idea to keep an eye on the beginning of the terminal line, to make sure it ends with this =# and not something like this -#. Another good practice for catching SQL syntax mistakes early is to pay attention to the result output after a command. If you make a new table you should get a message saying there's a new table, if you added an item you should see an insertion, if you do not get a response after running a command, something is wrong and you should stop and fix it.

--------------------------------------------------------------
## QUIZ Data in DAtabase and CRUDE Operations
### Question 1 of 4
Which of the following are real SQL commands that operate on rows in a table?
- (✔) INSERT
- (✔) DELETE
- (✔) UPDATE
- (✔) SELECT
- GET
- CREATE
- SWITCH
### Question 2 of 4
Match the CRUD command to its SQL command
|CRUD|SQL|
|----|----|
|Create|INSERT|
|Read|SELECT|
|Update|UPDATE|
|Delete|DELETE|
### Question 3 of 4
Match the filter to its description
|SQL Filter|Description|
|----------|-----------|
|WHERE|filter rows based on a specified condition|
|LIMIT|Cap the number of row responses from a query|
|BETWEEN|select data that is within a range of values|
|LIKE|filter data based on pattern matching|
|IS NULL/IS NOT NULL|check if a value is or is not null|
### Question 4 of 4
Match the SQL command to its type
|SQL Commands|Type|
|------------|-----|
|\q|Meta Command|
|SELECT * FROM herbs|Read Query|
|WHERE id='1'|Filter|
|INSERT INTO herbs ....|Create Query|
|LIMIT(10)|Filter|
|DELETE FROM herbs...|DELETE Query|
-------------------------------------------------

## Experiment!

In this workspace I have provided a space for you to experiment with building a database. There are no real goals for this workspace other than for you to be able to try out the various commands we have learned.
### Get comfortable with psql!
Below are some commands to try! And don't worry about messing anything up, this database is a safe testing ground. When in doubt, try it! Take note of what errors you get as well as what works.
## Task List
    - (✔) Connect to a database 
    - (✔) List the tables in the database you connected to\dt
    - (✔) Create a new row in each table
    - (✔) Delete a row in each table
    - (✔) Draw OUt schema of the database and its tables
    - (✔) Update any row in any table
    - (✔) Use a WHERE filter in a command
    - (✔) Use a LIKE filter in a command
    - (✔) Use the BETWEEN filter in a command

----------------------------------------------------------------------

## Postgres Sandbox
just as done before to reach to psql command terminal through typeing in the git terminal
```sh
psql -U postgres -h localhost -W
```
after that make ther next changes in the database
- Create a database with a name of your choosing.
- Connect to the database you creattetd\c <database_name>. The name of the database for this exercise is fictional_worlds.
- List the tables in the database you connected to \dt.
- Create a new row in each table.
- Delete a row in each table.
- Draw out a schema of the database and its tables.
- Update any row in any table.
- Use a WHERE filter in a command.
- Use a LIKE filter in a command.
- Use the BETWEEN filter in a command.
## Live example code asfollows
```sh
CREATE USER fictional_world_user WITH PASSWORD 'password123';
CREATE DATABASE fictional_world;
GRANT ALL PRIVILEGES ON DATABASE fictional_world TO fictional_world_user;
\c fictional_world
\dt
CREATE TABLE products(id SERIAL PRIMARY KEY, name VARCHAR(100), quantity integer, discription TEXT, issue_date DATE);
INSERT INTO products(name, discription, quantity, issue_date) VALUES ('cigar', 'harmful product', 1, '2021-01-02');
INSERT INTO products(name, discription, quantity, issue_date) VALUES ('monbar', 'arabic food product', 5, '2019-03-04');
SELECT * FROM products;
UPDATE products SET quantity=900 WHERE id =1;
SELECT * FROM products;
DELETE FROM products WHERE id=2;
SELECT * FROM products;
INSERT INTO products(name, discription, quantity, issue_date) VALUES ('cucamber', 'arabic food veg', 12, '2019-03-04');
INSERT INTO products(name, discription, quantity, issue_date) VALUES ('carrot', ' food veg', 53, '2019-01-04');
INSERT INTO products(name, discription, quantity, issue_date) VALUES ('shoe', 'wear product', 78, '2022-04-06');
SELECT * FROM products;
SELECT * FROM products LIMIT 2;
SELECT name FROM products WHERE issue_date BETWEEN '2023-01-01' AND '2020-01-01';
SELECT name FROM products WHERE discription LIKE '%food%';
INSERT INTO products(name, discription, quantity) VALUES ('carrot', ' food veg', 53);
SELECT name FROM products WHERE issue_date IS NULL;
SELECT name FROM products WHERE issue_date IS NOT NULL;
```
-------------------------------------------------------

## SQL Cheat Sheet, Tips, and Tricks
### Tips and Tricks
- You know that you're in the right database when you see the name of the database at the beginning of the terminal line.
- If you already know the name of the database you want to connect to, you can write psql name_of_database and that would be equivalent to psql postgres \c name_of_database
- Remember to steer clear of double quotes around strings in your queries!
### SQL Cheat Sheet
Meta Commands
```sh
\l List databases
\c Connect to a database
\dt Display Tables in a database
\q Quit out of psql to normal terminal
```
### Queries
- CREATE INSERT INTO worlds (name) VALUES ('Asgard');
- READ SELECT* FROM herbs;
- UPDATE UPDATE herbs SET sighting_date = '2021-01-10' WHERE id='1';
- DELETE DELETE FROM herbs WHERE id='1';
### Filters
- BETWEENSELECT * FROM trips WHERE start_date BETWEEN '2021-02-01' AND '2021-02-12';
- LIKE SELECT * FROM books WHERE title LIKE '%ship%';
----------------------------------------------------------
ALTER TABLE plants ADD FOREIGN KEY (region_id) REFERENCES region(id);
-----------------------------------------------------------
## Video Summary

- The Foreign Key is a column that relates each row to in the table to the primary key of another table
- Having a foreign key allows us to query for relationships between two tables of data

### Quiz Question
Which is the foreign key between these two tables?
* Table items
  - id
  - reference_number
  - category
  - description
* Table references
  - id
  - number
  - owner
  - schedule
- id
- number
- (✔) reference_number
- category
---------------------------------------------------------------
## Turning Ideas into Reality
#### Imagine this scenario:

My app is going to help people track their home electrical usage using bluetooth enabled electrical socket extensions, allowing users to view their most power hungry appliances, note which appliances have been running for an extended amount of time, know which outlets they use the most, and track their electrical usage throughout the year! Its going to be awesome! I have a front end in the works with a stunning user interface that everyone is going to love, and I need you to create the API to provide the data.

...Easy right? Or perhaps not. Part of being a software developer (and this really applies for both front and back end developers) is being able to translate abstract ideas for features or apps into concrete data structures. No where is this more true than in database design. It can be hard to take abstract ideas, identify their data needs, and meet those needs with tables and columns. In the video below, I take an abstract idea in the form of a task, discuss what data needs are implied, and update the database to complete the task.
### Task 1 - Find and Update
- A user let us know that there is a typo on one of the entries, but she can't edit it herself. Can you make sure that Dandelion is always spelled correctly?
- The requirement is to find the name with misspilling where we know that the error may be in the fourth char so firt we sue `LIKE` with the certfied chars find out the id then `UPDATE` the nmae which has the id. 
```sh
SELECT name FROM plants WHERE name LIKE 'Dan%';
UPDATE plants SET name = 'Dandelion' WHERE id = 11;
```
### Task 2 - Generating Reports
- I need to report on activity within the app to show stakeholders that we are getting more traction and involvement. Can we get total entries week by week for the last month?
- The requirement was to find out the count or frequency of repetation of engtiries that can be done through counting the records for every week that can be done using  `COUNT(*)` and `BETWEEN AND` as shown next
```sh
SELECT name, sighting_date FROM plants WHERE sigting_date BETWEEN '2021-01-04' AND '2021-01-31';
```
```sh
SELECT COUNT(*) FROM plants WHERE sigting_date BETWEEN '2021-01-04' AND '2021-01-10';
SELECT COUNT(*) FROM plants WHERE sigting_date BETWEEN '2021-01-11' AND '2021-01-17';
SELECT COUNT(*) FROM plants WHERE sigting_date BETWEEN '2021-01-18' AND '2021-01-24';
SELECT COUNT(*) FROM plants WHERE sigting_date BETWEEN '2021-01-25' AND '2021-01-31';
```
### Quiz Question
Which SQL keywords would you need to do the following task:
We need a list of all the users who logged in to the service yesterday before noon.

- INSERT 
- (✔) SELECT 
- UPDATE 
- DELETE 
- CREATE 
- SERIAL PRIMARY KEY 
- (✔) WHERE 
- (✔) BETWEEN 
- LIKE 
- IS NULL 
- IS NOT NULL
-----------------------------------------------------------------------
## Database Tasklist Exercise
### Step 1: Create the database

- First you will need to create a sightings database in psql.
- Step 2: Stakeholder task - Add a Table

In this challenge you have been given a task from stakeholders to work on the plant sightings database we created in the lesson. Here is the task they've assigned to you:
```
Our users like tracking their sightings of plants, but we have a lot of interest around tracking animal sightings as well. You need to add the ability to track animal sightings to the database.
```
An animal sighting should have the following information
- date of sighting
- type of animal seen
- number of animals seen
- sighting description
- region where the sighting took place
### Extra Challenge
For an extra challenge, try adding a simple users table and associate an animal sighting with a user. Don't worry about making a realistic users table, we'll cover these in much more detail later on in the course, just get the practice creating a table and adding a foreign key.
----------------------------------------------------------------------
## Exercise Solution
Well done completing the challenge! Below I have completed one implementation of this database so you can compare it to what you did - but remember - there is more than one good way to build a database!
### Part 1: Where to start
We have the instructions, but where to start? The requirements talk about storing animal sightings in the same way we store plant sightings, and this leaves us with some serious questions about what the next step should be, here are the options I see:
- We could make a table called sightings to hold all sightings and then add a type column to specify if the sighting was of an animal, plant, or any other sort of thing might be added in the future.
- We could add individual tables for animal and plant sightings.

You could really go either way, in a real world situation I would lean towards separate tables for each type of sighting, because it leaves more room for flexibility to change the structure of the tables separately.
### Part 2: Create the table
I was boring and decided to call this table animals, though creatures, mythical_creatures, or fantastic_beasts would all have been very good options.
### CREATE TABLE animals ...
Now for the slightly trickier part, deciding the rows. Right off the bat the first thing I know is that I'm going to add a serial primary key.
```sh
CREATE TABLE animals ( id SERIAL PRIMARY KEY ...);
```
- Good first step. Now we need to take a closer look at the other columns.
- The next one I pick out is the reference to region. Yes, this could be a VARCHAR ... but that isn't very helpful. This field needs to be a foreign key. So I add this:
```sh
CREATE TABLE animals ( id SERIAL PRIMARY KEY, region_id REFERENCES regions(id)...);
```
- The command above being part of the create table command is a little different than the `alter` table command we ran in the video, so you might have had to do some googling or you could have done a separate `alter` table query after creating this table. Either is fine, the above is just an example of what it looks like as part of a create query.
- From here its pretty smooth sailing, we just have to decide types and names for each column, here is what I did:
name: VARCHAR(100), `sighting_date: date, individuals: integer, description: text`
- The only important things here are that:
  - description should be the only text type
  - sighting date needs to be type date

### Part 3: Extra Challenge
- The extra challenge was to add a users table and attach a user to a sighting. For this, my users table is going to be very simple. The columns will be id and name since those are the only ones pertinent to this task.
- The only really important thing to make sure you did here, is that the foreign key constraint on the animals table needs to point to the ID column on the users table, and ID should be the PRIMARY KEY on the users table. It might be tempting to use name as the connecting column between the two tables, but a person's name is not guaranteed to be unique and should therefore never be used as a primary key.
- Its also worth noting that for users we would typically use a more complex type of ID than serial, but for our purposes here, its completely fine. We'll get more into details for user tables later in this course.

Here's an example user table for this exercise: `CREATE TABLE users ( id SERIAL PRIMARY KEY, name VARCHAR, email VARCHAR);`

The real goal of this extra challenge was to make sure you understood where the foriegn key should go. The foreign key belongs on the sighting
```sh
CREATE TABLE animals ( id SERIAL PRIMARY KEY, region_id REFERENCES regions(id), user_id REFERENCES users(id), individuals integer, sighting_date date, description text);
```

------------------------------------
## Solution on the sonline workspace
```sh
root@22dfdf827fc3:/home/workspace# su postgres
postgres@22dfdf827fc3:/home/workspace$ psql postgres
psql (9.5.23)
Type "help" for help.

postgres=# \l
                                List of databases
      Name      |  Owner   | Encoding  | Collate | Ct
ype |   Access privileges   
----------------+----------+-----------+---------+---
----+-----------------------
 bookshelf      | postgres | SQL_ASCII | C       | C 
    | =Tc/postgres         +
                |          |           |         |   
    | postgres=CTc/postgres+
                |          |           |         |   
    | student=CTc/postgres
 bookshelf_test | postgres | SQL_ASCII | C       | C 
    | =Tc/postgres         +
                |          |           |         |   
    | postgres=CTc/postgres+
                |          |           |         |   
    | student=CTc/postgres
 postgres       | postgres | SQL_ASCII | C       | C 
    | 
 template0      | postgres | SQL_ASCII | C       | C 
    | =c/postgres          +
                |          |           |         |   
    | postgres=CTc/postgres
 template1      | postgres | SQL_ASCII | C       | C 
    | =c/postgres          +
                |          |           |         |   
    | postgres=CTc/postgres(5 rows)

postgres=# CREATE USER sighting_user WITH PASSWORD 'password123';
CREATE ROLE
postgres=# CREATE DATABASE sightings;
CREATE DATABASE
postgres=# \c sightings
You are now connected to database "sightings" as user "postgres".
sightings=# CREATE TABLE regions (id SERIAL PRIMARY KEY, name VARCHAR(50));
CREATE TABLE
sightings=# CREATE TABLE users (id SERIAL PRIMARY KEY, name VARCHAR(50), email VARCHAR(50));
CREATE TABLE
```