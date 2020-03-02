# PostgreSQL

* [See all tables we create](https://stackoverflow.com/questions/2276644/list-all-tables-in-postgresql-information-schema)

```
SELECT table_name FROM information_schema.tables WHERE table_schema='public'
```

* When create the database with `docker-compose`, remember to delete the database if changing it.

* [Insert data to the database](https://stackoverflow.com/questions/20199569/pyodbc-insert-into-sql): Must commit the change

```
cursor.execute("insert into products(id, name) values (?, ?)", 'pyodbc', 'awesome library')
cnxn.commit()
```
