# Symmetric-Hash-Join
CSI3130 Final project. change hash join to Symmetric hash join with in PostgreSQL 8.1.7

1. Download postgres v8.1.7 from source.
    * Download from [the website](https://ftp.postgresql.org/pub/source/v8.1.7/postgresql-8.1.7.tar.gz)
2. Unpack the archive with the command: `$: tar -xvzf postgresql-8.1.7.tar.gz`
3. Replace the provided files with the ones in postgresql's source code
    * [createplan.c](./createplan.c) goes in /postgresql-8.1.7/src/backend/optimizer/plan/
    * [nodeHash.c](./nodeHash.c) goes in /postgresql-8.1.7/src/backend/executor/
    * [nodeHashjoin.c](./nodeHashjoin.c) goes in /postgresql-8.1.7/src/backend/executor/
    * [execnodes.h](./execnodes.h) goes in /postgresql-8.1.7src/include/nodes/
4. Change directory to /postgresql-8.1.7/
5. Install gcc 4.7, zlib1g, zlib1g-dev, libreadline6 and libreadline6-dev if not done already.
    * `$ sudo apt-get install gcc-4.7`
    * `$ sudo apt-get install zlib1g zlib1g-dev`
    * `$ sudo apt-get install libreadline6 libreadline6-dev`
6. `$ ./configure CC='gcc-4.7 -m64' --enable-debug -enable-depend`
7. `$ make`
8. `$ make install` Try with `sudo` if this doesn't work
9. If `$ ls -l /usr/local/pgsql/` shows the bin, doc, include, lib, man and share directories `$ adduser postgres` w/ a password of choice.
10. `$ mkdir /usr/local/pgsql/data` `$ chown postgres:postgres /usr/local/pgsql/data`
11. If the previous worked `$ ls -ld /usr/local/pgsql/data` will show the directory with the user postgres' ownership
12. `$ su - postgres` or login as the user postgres
13. `$ /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data` to initialize postgreSQL data directory
14. `$ /usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data >logfile 2>&1 &` to start the db. Try `$ cat logfile` to see if it started.
15. `$ /usr/local/pgsql/bin/createdb test` to create a schema with the name test
16. `$ /usr/local/pgsql/bin/psql test`to start the PostgreSQL terminal in the schema test.

The steps shown are for when you first set up your postgres environment, if you already have this set up then do the following:
- `$ /usr/local/pgsql/bin/pg_ctl -D /usr/local/pgsql/data -l logfile start`
- `$ /usr/local/pgsql/bin/psql test` or replace `test` with your schema name.

---
