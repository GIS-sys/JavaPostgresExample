# Based on
Amazing article [Spring Boot JdbcTemplate and PostgreSQL example: CRUD Rest API](https://www.bezkoder.com/spring-boot-jdbctemplate-postgresql-example/)

# How to

0) create psql user `testuser` with password `testpass` and grant priviliges on database `testdb`

1) create table:

```psql
CREATE TABLE tutorials
(
    id BIGSERIAL PRIMARY KEY NOT NULL,
    title VARCHAR(255),
    description VARCHAR(255),
    published BOOLEAN
);
```

You may need to connect via

```
sudo -u postgres psql -d testdb
\c "host=localhost port=5432 dbname=testdb user=testuser password=testpass
```

2) run: ./mvnw spring-boot:run

3) use curl to try requests:

```bash
curl -i -X GET http://localhost:8080/api/tutorials
curl -i -X POST http://localhost:8080/api/tutorials -H "Content-Type: application/json" -d '{"title": "a", "description": "b"}'
curl -i -X GET http://localhost:8080/api/tutorials
curl -i -X PUT http://localhost:8080/api/tutorials/1 -H "Content-Type: application/json" -d '{"title": "a", "description": "b", "published": true}'
curl -i -X GET http://localhost:8080/api/tutorials
```
