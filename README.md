`docker-compose up -d`

```
[+] Running 12/12
 - mysql-57 Pulled                                                                25.5s
   - a4b007099961 Pull complete                                                    4.1s
   - e2b610d88fd9 Pull complete                                                    4.2s
   - 38567843b438 Pull complete                                                    4.5s
   - 5fc423bf9558 Pull complete                                                    4.8s
   - aa8241dfe828 Pull complete                                                    5.1s
   - cc662311610e Pull complete                                                    6.8s
   - 9832d1192cf2 Pull complete                                                    6.9s
   - 3f242378e320 Pull complete                                                    7.0s
   - cc65503c0186 Pull complete                                                   16.7s
   - ce8944d50437 Pull complete                                                   16.9s
   - 597d59a9a424 Pull complete                                                   17.0s
[+] Running 2/2
 - Network demo-docker-compose-mysql-57_default  Created                           0.1s
 - Container mysql                               Started                           1.7s
```

`docker compose logs mysql --follow`

```
mysql  | 2022-03-29 04:01:35+00:00 [Note] [Entrypoint]: Creating user mysqluser
mysql  |
mysql  | 2022-03-29 04:01:35+00:00 [Note] [Entrypoint]: /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/init-script.sql
mysql  |
```

```
mysql  | 2022-03-29T04:01:38.297479Z 0 [Note] Event Scheduler: Loaded 0 events
mysql  | 2022-03-29T04:01:38.297846Z 0 [Note] mysqld: ready for connections.
mysql  | Version: '5.7.37'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
```

`mysql -h localhost -P 3306 -u root -pmysqlrootpassword -e "select * from demo.demo_table"`

```
mysql: [Warning] Using a password on the command line interface can be insecure.
+----+------+
| id | text |
+----+------+
|  1 | Demo |
+----+------+
```

`docker-compose down`

```
[+] Running 2/2
 - Container mysql                               Removed                           2.5s
 - Network demo-docker-compose-mysql-57_default  Removed                           0.2s
```
