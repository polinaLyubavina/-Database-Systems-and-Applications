# Lab 9: Indices


## Part 1 - Selecting Indexes

### A database contains the following table for former-employee records:
- Additional indexes needed: Start Date and End Date because you need to do lookup by start date and/or end date.

### A database contains the following table for tracking student grades in classes
- Additional indexes needed: Grade because you need to be able to do lookups by the grade. No additional indexes are needed because the className and studentID are already primary keys.

### Using the same grade database, but now the common queries are:
- Additional indexes needed: Grade because you need to be able to do lookups by the grade. No additional indexes are needed because the className and studentID are already primary keys.

### Queries on the chess database
- Additional indexes needed: the Elo and whiteplayer need to be made into 2 indexes so you can lookup by Elo rating and join on whiteplayer efficiently. No additional indexes are needed because the pID is already a primary key.

### Queries on the public Library database
- Additional indexes needed: None because the only column in common between the two tables is Serial, which happens to be in the primary key of both the tables already.

### More library queries:
- Additional indexes needed: We'd need to add an index on CheckedOut.CardNum, since it's used for a lookup in the first query, and for joining in the second query. The other lookups and joins are already accounted for in primary keys.

### Still more library queries
- Additional indexes needed: This is basically a natural join of titles and inventory. To speed this up, we could add an index on Inventory.ISBN. Titles.ISBN, is already part of the primary key.

## Part 2 - B+ Tree Index Structures

### Students table:
- How many rows of the table can be placed into the first leaf node of the primary index before it will split? 
**You can fit 273 before the node will split**

- What is the maximum number of keys stored in an internal node of the primary index? 
**internal nodes have no keys**

- What is the maximum number of rows in the table if the primary index has a height of 1? 
**since the tree has a height of 1, the root node will not contain any key values. Instead, the root node will have pointers to children nodes. These children nodes will each have 273 rows inside them. The maximum number of rows is 79,989**

- What is the minimum number of rows in the table if the primary index has a height of 1? 
**minimum number of rows is 274 rows**

- If there is a secondary index on Grade, what is the maximum number of entries a leaf node can hold in the secondary index? 
**A leaf node in the secondary index would be able to hold 273 entries.**

### Another table
- What is the maximum number of leaf nodes in the primary index if the table contains 48 rows? 
**maximum number of leaf nodes is 4096/128 = 32** 

- What is the minimum number of leaf nodes in the primary index if the table contains 48 rows? 
**minimum number of leaf nodes is 4096/128/2 = 16**
