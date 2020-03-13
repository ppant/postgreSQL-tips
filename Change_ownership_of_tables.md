Changing ownership of all the tables
Step 1 : Login with postgre user and run select 'alter table '|| tablename ||' owner to postgres;' from pg_tables where schemaname = 'public';
Step 2: Copy output of step 1 and run it. Check with \d if all tables ownership is changed to postgres

Enjoy the automation!
