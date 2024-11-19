# Created a postgres database and loading a file using docker

```console
docker run --name postgresql -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -v postgres:/var/lib/postgresql/data -d postgres:14.7
```

Create a database called fastlight2, using pgAdmin and make sure that psql is on the path

add extension pg_trgm

```console
psql -d fastlight2 -U postgres -f .\fastlight2_day1.sql
```
