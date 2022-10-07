#### SQL Databases
Are tabular/relational. They use tables with rows and columns to store information. 

![[Pasted image 20220608120129.png]]

Each new piece of information stored adds a new column that affects the whole table. 

#### NoSQL Databases
Use documents to store data. Each document is like a Row from a table in SQL. Documents can take any form or structure, and changes to one document do not affect the others. You can use simple key value pairs or more likely [[JSON]] formatted files. 

A group of documents in a NoSQL database is referred to as a **Collection**

#### Queries
SQL Database queries follow this format
``` SQL
SELECT * FROM Person WHERE Age > 10
```

NoSQL Database queries follow this format
``` JSON Query
db.persons.find( { age: { $gt: 10} } )
```

#### SQL Examples
- [[MySQL]] 
- PostgreSQL
- MsSQL

#### No SQL Examples
- [[MongoDB]]
- DynamoDB
- Cassandra