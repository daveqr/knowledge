# Mongo DB

## Quick Commands

* List all collections (tables):

	```
	> show tables
	```

* Drop a collection (table):

	```
	> db.todos.drop()
	```

* Switch to a specific database:

	```
	> use <db>
	```
		
* Find all documents (rows) in a collection (table):

	```
	> db.table.find()
	```

* Delete all documents (rows) from a collection (table):

	```
	> db.table.deleteMany({})
	```
	
* Delete multiple documents (rows) from a collection (table), specify a filter condition:

	```
	> db.table.deleteMany({ status: "inactive" })
	```	

## Other Stuff

### CRUD Operations
Create (Insert):

insertOne(): Inserts a single document into a collection.
insertMany(): Inserts multiple documents into a collection.
Read (Query):

find(): Retrieves documents from a collection based on a query condition.
findOne(): Retrieves a single document from a collection based on a query condition.
Projection: Use the projection parameter to specify which fields to include or exclude in the results.
Comparison Operators: MongoDB supports various comparison operators like $eq, $ne, $gt, $lt, etc., for more complex queries.
Update:

updateOne(): Updates a single document in a collection that matches a query condition.
updateMany(): Updates multiple documents in a collection that match a query condition.
$set: Operator to set the value of a field in an update operation.
$unset: Operator to remove a field from a document in an update operation.
$inc: Operator to increment a numeric field's value.
Delete:

deleteOne(): Deletes a single document in a collection that matches a query condition.
deleteMany(): Deletes multiple documents in a collection that match a query condition.

### Schema Design
schema design best practices, including embedding vs. referencing documents, and considerations for designing collections and documents to optimize performance.

### Indexes
create indexes in MongoDB and their importance for improving query performance. Include information on different types of indexes and when to use them.

Aggregation Framework: Describe how to perform complex data transformations and aggregations using MongoDB's aggregation framework.

Transactions: If applicable, explain how to work with transactions in MongoDB, especially when dealing with multiple operations that need to be atomic.

Security: Cover security topics, including user authentication, authorization, role-based access control, and network security configurations.

Replication and Sharding: If using MongoDB in a distributed environment, provide information on setting up replication and sharding for scalability and high availability.

Backup and Restore: Discuss backup and restoration strategies using MongoDB tools like mongodump and mongorestore.

Monitoring and Performance Optimization: Share tips and best practices for monitoring MongoDB performance using tools like MongoDB Atlas, and techniques for optimizing query performance.

Error Handling and Troubleshooting: Include information on common errors and troubleshooting techniques.
