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

## Writing query output to a CSV file:
\o 'tmp/logs/query_out_dump.csv'

## After this operation all the query results will be stored in a CSV file.
Using console again for query output:
\o

## Check the size of a postgreSQL database
SELECT pg_size_pretty( pg_database_size('dbname') );
*replace **dbname** with the correct dbname*
