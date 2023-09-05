# Databases

Indexes are database structures used to improve the speed and efficiency of data retrieval operations. There are two primary types of indexes: clustered indexes and non-clustered indexes, each serving a different purpose.

Clustered Index:

* A clustered index determines the physical order of data rows in a table.
* There can be only one clustered index per table because the physical order of rows can't be changed simultaneously in multiple ways.
* When you create a clustered index on a table, the data rows are rearranged and stored in the same order as the index key. This means that the data in the table is physically sorted based on the clustered index key.
* Typically, the primary key of a table is used as the clustered index, but it's not mandatory. If a table doesn't have a clustered index, it is referred to as a heap, and data rows are stored in no particular order.
* Because the data rows are stored in the order of the clustered index, queries that use the clustered index key for filtering or sorting can be very fast, as SQL Server can perform binary searches to locate the data.

Non-Clustered Index:

* A non-clustered index is a separate structure that contains a copy of selected columns from the indexed table along with a reference to the actual data row's location.
* Multiple non-clustered indexes can be created on a single table.
* Non-clustered indexes are generally used to improve the performance of SELECT queries that filter or sort data based on columns that are not part of the clustered index.
* When you create a non-clustered index, you specify the columns you want to include in the index and the order in which they should be sorted.
* Non-clustered indexes are slower for retrieving data compared to clustered indexes because they involve an additional lookup step to find the actual data rows after locating the indexed values in the index.

In summary, a clustered index determines the physical order of data rows in a table and is often associated with the primary key of the table. Non-clustered indexes are separate structures used to speed up data retrieval for queries that filter or sort data based on columns not part of the clustered index. It's common to have both types of indexes on a table to optimize various types of queries.





