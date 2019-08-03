
# Chapter 3

### Bring up the config server up
```
mongod -f csrs_1.conf
mongod -f csrs_2.conf
mongod -f csrs_3.conf
```



### Config the replica set of the config servers
```
# Connect to config server
mongo --host localhost:26000

# Start the replica set
rs.initiate()

# Create the admin user
use admin
db.createUser({ user: "m103-admin", pwd: "m103-pass", roles: [ {role: "root", db: "admin"} ] })

# Change the db authenticated
db.auth("m103-admin", "m103-pass")

# Add the replica sets
rs.add("192.168.103.100:26002")
rs.add("192.168.103.100:26003")
```


### Start the mongos server
```
mongos -f mongos.conf

# Connect it
mongo --port 26000 --username m103-admin --password m103-pass --authenticationDatabase admin
```


### Start or restart the server with sharding config
```
mongod -f node1.conf
mongod -f node2.conf
mongod -f node3.conf

# Start the replica set
rs.initiate()

# Create the admin user
use admin
db.createUser({ user: "m103-admin", pwd: "m103-pass", roles: [ {role: "root", db: "admin"} ] })

# Change the db authenticated
db.auth("m103-admin", "m103-pass")

# Add the replica sets
rs.add("192.168.103.100:27012")
rs.add("192.168.103.100:27013")
```


### Add the sharded server
```
# Connect to the replication server
mongo --port 26000 --username m103-admin --password m103-pass --authenticationDatabase admin

# Add the repl server 
sh.addShard("m103-repl/192.168.103.100:27012")

```