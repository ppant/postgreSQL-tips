## Create a new database name testdb
createdb <dbname>
createdb testdb

## Remove a PostgreSQL database
dropdb <dbname>
dropdb testdb

## Backing up a PostgreSQL database
su - postgres
pg_dump --blob -Fc testdb -f /var/lib/pgsql/backups/testdb_backup

## Restoring PostgreSQL database from back up dump
pg_restore --dbname=testdb /var/lib/pgsql/backups/testdb_backup

## Writing query output to a CSV file
\o 'tmp/logs/query_out_dump.csv'

## After this operation all the query results will be stored in a CSV file
\o

## Check the size of a postgreSQL database
SELECT pg_size_pretty( pg_database_size('dbname') )
*replace **dbname** with the correct dbname*

## CAST usage
### PostgreSQL CAST To Convert a Value of One Type to Another
select remind_date from reminder where remind_date::date >='2037-12-31';

CAST ( expression AS target_type );

First, specify an expression that can be a constant, a table column, an expression that evaluates to a value. Then, specify the target data type to which you want to convert the result of the expression.
PostgreSQL type cast :: operator Besides the type CAST syntax, you can use the following syntax to convert a value of one type into another:

expression::type

See the following example:
SELECT
  '100'::INTEGER,
  '01-OCT-2015'::DATE;
Notice that the cast syntax with the cast operator (::) is PostgreSQL-specific and does not conform to the SQL standard

###Example: Select date field using LIKE
select remind_date from reminder where CAST(reminder.remind_date AS VARCHAR) like '2020-02-25%' order by remind_date desc;




