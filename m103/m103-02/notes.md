

# Chapter 2

### Bring up the servers
```
mongod -f mongod-repl-1.conf
mongod -f mongod-repl-2.conf
mongod -f mongod-repl-3.conf
```

### Initiate replica set
```
rs.initiate()
```

### Adding other members to replica set:
```
rs.add("192.168.103.100:27012")
rs.add("192.168.103.100:27013")
```


### Commands to check the status of replication
```
rs.status()
rs.isMaster()
db.serverStatus()['repl']
rs.printReplicationInfo()
```


### Stepping down the current primary:
```
rs.stepDown()
```
