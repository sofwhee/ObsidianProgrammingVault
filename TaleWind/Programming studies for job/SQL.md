https://www.dbvis.com/wp-content/uploads/2024/04/SQL-Cheat-Sheet.pdf

A querying language for navigating databases.

**Schema** - A blueprint that defines the rules or constraints in a database.
Tables are just `Dicts` where key = column and value = datatype.
**Constraints** (for Columns) - unique, not null, primary key, enum
- **Primary Key** (constraint) - can't be null + must be unique
**Normalized Data Structure** 
- Every table is a unique entity. `Rooms` doesn't need to store any `user `info. Just a `user ID`.
- Unique ID can be saved on another table, to represent a one-to-one/many relationship.
- Like taking a car apart into its individual parts. When it's time to make a car, you join the parts together.
**Identifier** - Name of the table.
**Identifiers** - Name of columns

**Varchar** - small strings
**Text** - larger unpadded strings

**Pattern** - a searchable pattern.
**Index** - A consolidated search pattern.
- A lookup table that allows you to retrieve data faster.
- Like an index in the back of a textbook. 
- Helps you find things without having to scan the entire dataset.
- Comes at a cost of slower writes.
- Takes up additional memory.

**Relational Data**
- One-To-Many, One-To-One, Many-to-Many
**Primary Key** - Reference to an ID in home table.
**Foreign Key** - Reference to an ID in another table.

**REFERENCES** - Don't delete related data
- Ensures a value entered into a foreign key column must already exist in the primary key column of the referenced table
- Stops you from orphaning a record. You can't delete a row in the parent table if there are still related rows in the child table.
- Primary way to build one-to-one or one-to-many.

**AS** - basically just defines a table as a variable with a name.
## Example Usage

```SQL
-- @block
CREATE TABLE Users(
	id INT PRIMARY KEY AUTO_INCREMENT,
	email VARCHAR(255) NOT NULL UNIQUE, -- constraints
	bio TEXT,
	country VARCHAR(2) -- max length of 2
);
```

![[Pasted image 20260507145007.png]]

```SQL
-- Insert a row into the table
-- @block
INSERT INTO USERS (email, bio, country)
VALUES (
	'hello@world.com',
	'i love strangers!',
	'US'
);

-- Insert multiple rows
INSERT INTO USERS (email, bio, country)
VALUES (
	('hello@world.com', 'i love strangers!', 'US')
	('hello@world.com', 'i love strangers!', 'US')
	('hello@world.com', 'i love strangers!', 'US')
);
```

```SQL
-- Select all
SELECT * FROM Users;
-- Select two keys
SELECT email, id FROM Users;

WHERE country = 'US' -- Run conditional logic with WHERE. AND or OR available.
AND email LIKE 'hello%' -- Pattern. LIKE is basically full text search.

ORDER BY id ASC
LIMIT 2; -- limit rows returned
--
```

``` SQL
CREATE INDEX email_index ON Users(email); -- Users table, email column
```

```SQL
CREATE TABLE Rooms(
	id INT AUTO_INCREMENT,
	street VARCHAR(255),
	owner_id INT NOT NULL,
	PRIMARY KEY (id),
	FOREIGN KEY (owner_id) REFERENCES Users(id)
	-- REFERENCES ensures that the foreign key is read-only.
);
```

## Join

![[Pasted image 20260507153302.png]]

```SQL
-- Fetch all rooms that belong to a user
SELECT * FROM USERS
INNER JOIN ROOMS
ON Rooms.owner_id = Users.id;

-- Fetch all users, regardless of room ownership
SELECT * FROM USERS
LEFT JOIN ROOMS
ON Rooms.owner_id = Users.id

-- Fetch all rooms, regardless of user ownership
SELECT * FROM USERS
Right JOIN ROOMS
ON Rooms.owner_id = Users.id

-- Fetch all rooms, regardless of user association
SELECT * FROM USERS
Right JOIN ROOMS
ON Rooms.owner_id = Users.id

-- FULL OUTER JOIN is not supported in MYSQL, but it's the whole two tables.
```

### How does a user book a room from another user?

Create a "Bookings" table.
It has a guest id, room id, and then check in time.
Guest id and room id are foreign keys.
That allows us to make complex relationships.

Run joins through the bookings table:

```SQL
-- Rooms a user has booked
SELECT
	guest_id,
	street,
	check_in
FROM Bookings
INNER JOIN ROOMS ON Rooms.owner_id = guest_id
WHERE guest_id = 1; -- Guest we are checking on

-- or
-- ...
WHERE room_id = 2; -- Guests who stayed in a room
```

## General Usage

SELECT * FROM celebs;

`*` means you're searching for everything in it. 
celebs is a relational database - a database that organizes info into one or more tables. Tables are sometimes referred to as relations.

Types:
`INTEGER`, `TEXT`, `DATE` YYYY-MM-DD, `REAL` decimal value

```SQL
CREATE TABLE table_name (
	column_1 data_type,
	column_2 data_type,
	column_3 data_type
);
```
`CREATE TABLE` is a *clause*.

clause - clauses are written in CAPITAL LETTERS. Clauses can also be referred to as commands.

INSERT - insert a new row in a table.

## Advanced

![[Pasted image 20260504085826.png]]

## Core Validation Techniques

- Presence Check
- Built-in Filters
- Pattern Matching
- String Length

**Sanitization**
- Different from validation
- Removes/ Encodes illegal characters
	- `trim()`, `htmlspecialchars()`
- Prevents XSS and other attacks
## Etc