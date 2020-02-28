# PostgreSQL

* [See all tables we create](https://stackoverflow.com/questions/2276644/list-all-tables-in-postgresql-information-schema)

```
SELECT table_name FROM information_schema.tables WHERE table_schema='public'
```

* When create the database with `docker-compose`, remember to delete the database if changing it.
