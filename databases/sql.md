# SQL

## MySQL

```sql
-- start via docker
docker run --name=mystuff-mysql -d -e MYSQL_ROOT_PASSWORD=trallalla -e MYSQL_DATABASE=my_stuff -e MYSQL_USER=my_stuff -e MYSQL_PASSWORD=my_stuff -p 3306:3306 mysql:8

-- create database + user
CREATE DATABASE IF NOT EXISTS my_stuff;
CREATE USER IF NOT EXISTS 'my_stuff'@'%' IDENTIFIED BY 'my_stuff';
GRANT ALL PRIVILEGES ON my_stuff.* TO 'my_stuff'@'%';

-- disable password plugin
uninstall plugin validate_password;
```

* [https://stackoverflow.com/questions/5239376/mysql-localhost-127-0-0-1-problem](https://stackoverflow.com/questions/5239376/mysql-localhost-127-0-0-1-problem)


## PostgreSQL

```bash
# db backup (redirected to measure size)
pg_dump -h localhost -U <username> -Fc <dbname> > mydump.tar | wc -l
```