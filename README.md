# http-python-rw-cassandra

Bring up Cassandra

```
docker run --name local-cassandra -d cassandra:3.10
```

Enter Cassandra Shell

```
docker run -it --link local-cassandra:cassandra --rm cassandra:3.10 cqlsh cassandra
```
