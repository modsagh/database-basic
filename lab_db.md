# Introdaction to SQLAlchemy

The purpose of these laboratory classes is to familiarize participants with the basic techniques of working with [SQLAlchemy](https://www.sqlalchemy.org/).

The scope of this classes:
- connection to a database (especially remote database),
- creating simple select in ORM,
- using query results in a program,
- adding where clause to query.

SQLAlchemy is the Python SQL toolkit and Object Relational Mapper that gives application developers the full power and flexibility of SQL.

It provides a full suite of well known aenterprise-level persistence patterns, designed for efficient and high-performing database access, adapted into a simple and Pythonic domain language.

Object Relational Mapper (ORM) is a programming technique for converting data between incompatible type systems using object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language.


## Connection SQLAlchemy with database

To connection a database with a program with the basic version we need to use the following script:

```python
from sqlalchemy import create_engine

db_string = "database_type://user:password@database_url:port/database_name"

db = create_engine(db_string)
```
where:
- *databae_type* is the name of database driver, more details you can read [here](https://docs.sqlalchemy.org/en/13/core/engines.html#database-urls),
- *user* - name of user in database,
- *password* - password to database,
- *database_url* - url address to database,
- *port* - port to database connection,
- *database_name* - name of database.  

*[create_engine](https://docs.sqlalchemy.org/en/13/core/connections.html)* is just interface to connection database with program.


## SQLAlchemy query

The basic select in SQLAlchemy has form:

```python
stmt = 'select * from table'

# Execute the statement and fetch the results
results = db.execute(stmt).fetchall()

# Print results
print(results)
```
Function *execute* make a request to a database and *fetchall* method get our results from an executed query. But in this case we don't use ORM propertis. More correctly is use structur:

```python
from sqlalchemy import select

stmt = select([table])

# Print the SQL query string
print(stmt)

# Execute the statement and fetch with limit the results 
results = db.execute(stmt).fetchmany(size=10)
print(results)
```
In this case, the ORM system creates a query based on information in object *table*.

### Read result from query
The variable *results* can be read as follows:

1. Print  n row of the results:

```python
print(results[n])
```
2. Print the first column of a n row by accessing it by its index:

```python
print(first_row[:][n])
```
3. Print the column by name of the a n row by using its name

```python
print(results[n][name])
```

### Adding constraint to query
 Adding a restriction to a query involves entering the *where* function as follows:
 ```python
stmt = select([table])

# Add a where clause to filter the results
stmt = stmt.where(table.columns.column_name == 10)

# Execute the query to retrieve all the data returned: results
results = db.execute(stmt).fetchall()

# Loop over the results and print the column_name_1 and column_name_2
for result in results:
    print(result.column_name_1, result.column_name_2)
 ```
 
 
## Exercises:
Write script to conection to databases and perform the following tasks: 

For PostgreSql database structure are describe [here](https://www.postgresqltutorial.com/postgresql-sample-database/):
1. Create a script to connection with database.
1. How many categories of films are in the rental?
1. Display list of categories with limit 2.
1. Find the oldest and youngest film in rental.
1. Find all actor with a name: Olympia, Julia, Ellen. How can you check correction of your query?