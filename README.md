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
    PRIMARY KEY (id, ts)
);
```
