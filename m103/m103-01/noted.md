
# Chapter 1


### Using localhost exception to create admin user
when creating a new mongo it allows you to connect through localhost just to create the admin user

```
# connect with mongo
mongo --host localhost:27000

# then create the user
use admin
db.createUser({ user: "m103-admin", pwd: "m103-pass", roles: [ {role: "root", db: "admin"} ] })

# If you want to connect
mongo --host localhost:27000 --authenticationDatabase admin --username 'm103-admin' --password 'm103-pass'
```