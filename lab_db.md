# Introdaction to SQLAlchemy

The purpose of these laboratory classes is to familiarize participants with the basic techniques of working with Pandas with SQL.

The scope of this classes:
- connection to a database (especially remote database),
- using query results in a program,
- adding where clause to query.

It provides a full suite of well known aenterprise-level persistence patterns, designed for efficient and high-performing database access, adapted into a simple and Pythonic domain language.

Object Relational Mapper (ORM) is a programming technique for converting data between incompatible type systems using object-oriented programming languages. This creates, in effect, a "virtual object database" that can be used from within the programming language.


## Connection with database

To connection a database with a program with the basic version we need to use the following script:

```python
import psycopg2 as pg
import pandas as pd

connection = pg.connect(host='...', port='...', dbname='...', user='...', password='...')
```
where:
- *user* - name of user in database,
- *password* - password to database,
- *host* - url address to database,
- *port* - port to database connection,
- *dbname* - name of database.  

*[create_engine](https://docs.sqlalchemy.org/en/13/core/connections.html)* is just interface to connection database with program.


## Query

The basic select in PANDAS has form:

```python
df = pd.read_sql('select * from city',con=connection)
print(df)

``` 

## Exercises:
Write script to conection to databases and perform the following tasks: 

For PostgreSql database structure are describe [here](https://www.postgresqltutorial.com/postgresql-sample-database/):
1. Create a script to connection with database.
1. How many categories of films are in the rental?
1. Display list of categories with limit 2.
1. Find the oldest and youngest film in rental.
1. Find all actor with a name: Olympia, Julia, Ellen. How can you check correction of your query?
