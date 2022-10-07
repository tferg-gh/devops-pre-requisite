MongoDB is a noSQL database. It stores data as a document. Multiple documents together for a collection. Multiple collections for a database and you can have multiple databases as part of a server. 

MongoDB comes in two forms, the free community edition and the paid for enterprise edition. You can also install MongoDB on-premise or as a cloud managed SaaS platform. 

#### Installation
https://www.mongodb.com/docs/manual/installation/#mongodb-installation-tutorials

First you need to create the repo for Yum, make this file: 
```
/etc/yum.repos.d/mongodb-org-5.0.repo
```
And add this to it:
```
[mongodb-org-5.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/5.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-5.0.asc
```
Then using yum do:
```
sudo yum install -y mongodb-org
```

MongoDB is installed as a service

#### Installation Location
```dir
/usr/bin/mongod
```

#### Start the service
``` bash
systemctl start mongod
```

#### Service status
```shell
systemctl status mongod
```

#### Log Location
```dir
/var/log/mongodb/mongod.log
```
The log has information regarding the DB version, the the PID and the Port/IP it is listening on. By default the IP is **127.0.0.1** and the port is **27017**

#### Check Version
```shell
mongod --version
```

#### Server Configuration
```dir
/etc/mongod.confg
```

#### Mongo Shell
Use this to login to the shell and interact with the databases on the server
``` Mongo Shell
mongo
```
By default MongoDB doesn't have any access controls configured, anyone can access anything. 

Mongo Shell uses JavaScript, so all the commands are going to be JavaScript commands.

#### List Databases
``` Mongo
show dbs
```

#### Create/Switch database
``` Mongo
use school
```

#### Show current database
``` Mongo
db
```

#### Create collection
```js
db.createCollection("persons")
```

#### Show collections
``` Mongo
show collections
```

#### Insert data
```js
db.persons.insert({
	"name":"John Doe",
	"age":45,
	"location":"New York",
	"salary":"50000"
})
```
This creates a document within the collection in the database

#### Query database
```js
db.persons.find()
```

**Note:** Every document is given a unique ID at the beginning in the form of "_id": ObjectId("UNIQUEID"),

```json
db.persons.find({"name": "John Doe"})
```
