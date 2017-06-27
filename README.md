# http-python-rw-cassandra

Bring up Cassandra

```
docker run --name local-cassandra -d cassandra:3.10
```

Enter Cassandra Shell

```
docker run -it --link local-cassandra:cassandra --rm cassandra:3.10 cqlsh cassandra
```

Create Keyspace

```
CREATE KEYSPACE "application_n" WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 1};
```

Use Keyspace

```
USE "application_n";
```

Create Table

```
CREATE TABLE "stats" (
    id int,
    ts timestamp,
    value float,
    PRIMARY KEY (id, ts))
WITH CLUSTERING ORDER BY (ts DESC);
```

Insert Two Rows

```
INSERT INTO stats (id, ts, value) VALUES (1, toTimestamp(now()), 0.1);
INSERT INTO stats (id, ts, value) VALUES (1, toTimestamp(now()), 0.2);
```

Select Latest Row

```
SELECT * FROM stats limit 1;
```

Exit Cassandra Shell

```
exit
```

Launch R HTTP API

```
python r.py
```

Use R HTTP API

```
curl http://localhost:8081/
```

Launch W HTTP API

```
python w.py
```

Use W HTTP API

```
curl http://localhost:8082/
```
