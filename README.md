# convox/postgres

Mysql docker image based on Alpine Linux

This repo builds a docker image that accepts MYSQL_USER, MYSQL_PASSWORD,
and MYSQL_DATABASE env vars, in addition to the same env vars as the
[official mysql build](https://registry.hub.docker.com/_/mysql/) but
with a much smaller footprint. It achieves that by basing itself off the great
[alpine](https://github.com/gliderlabs/docker-alpine) docker image by GliderLabs.

## Usage

```bash
$ docker run -p 3306:3306 convox/mysql
$ docker exec -it <container id> mysql --user=mysql -p
Enter password: password
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 4
Server version: 10.1.12-MariaDB MariaDB Server

Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| app                |
| information_schema |
| test               |
+--------------------+
3 rows in set (0.00 sec)

MariaDB [(none)]> use app;
Database changed

MariaDB [app]> show tables;
Empty set (0.00 sec)
```

## Why?

Parameterizing MYSQL_USER, MYSQL_PASSWORD, and MYSQL_DATABASE is useful
for [linking containers](https://docs.docker.com/userguide/dockerlinks/) together.

# Build

```bash
$ make build
```

## License

Apache 2.0 &copy; 2015 Convox, Inc.

## Credits

Originally forked from [kiasaki/docker-alpine-postgres](https://github.com/kiasaki/docker-alpine-postgres)
