# Data Manipulation Language (DML)

**DML** stands for **Data Manipulation Language**.

In SQL, DML commands are used to retrieve and modify data stored in database tables. The main DML commands are:

- **INSERT** – adds new rows to a table.
- **SELECT** – retrieves data from a table.
- **UPDATE** – modifies existing data.
- **DELETE** – removes rows from a table.

---

## INSERT

The `INSERT` command adds new rows to a table.

### Inserting Data

A row can be inserted using the `INSERT INTO` statement:

```sql
INSERT INTO Customer(customerName, street, customerCity)
VALUES ('Smith', 'Derby', 'Leicester');
```

The values are inserted into the columns listed in the `INSERT INTO` clause.

The order of the columns can be changed, provided the values match the listed columns:

```sql
INSERT INTO Customer(street, customerCity, customerName)
VALUES ('Derby', 'Leicester', 'Smith');
```

`'Derby'` is inserted into `street`, `'Leicester'` into `customerCity`, and `'Smith'` into `customerName`.

If a column is omitted and does not have a default value, Oracle stores `NULL` in that column:

```sql
INSERT INTO Customer(customerName, customerCity)
VALUES ('Smith', 'Leicester');
```

Since no value is provided for `street`, it will be stored as `NULL`.

---

## SELECT

The `SELECT` command retrieves data from one or more tables.

### Example

Find the address details for the customer Smith:

```sql
SELECT street, customerCity
FROM Customer
WHERE customerName = 'Smith';
```

### Selecting All Columns

The `*` wildcard returns every column in the table:

```sql
SELECT *
FROM Customer;
```

### Selecting Specific Rows

The `WHERE` clause filters rows that match a condition:

```sql
SELECT customerName
FROM Customer
WHERE customerCity = 'Leicester';
```

This returns only customers who live in Leicester.

---

## UPDATE

The `UPDATE` command changes existing data in a table.

### Example

Change Smith's city from Leicester to Nottingham:

```sql
UPDATE Customer
SET customerCity = 'Nottingham'
WHERE customerName = 'Smith';
```

The `WHERE` clause determines which rows are updated.

### Updating All Rows

If the `WHERE` clause is omitted, every row in the table is modified:

```sql
UPDATE Customer
SET customerCity = 'Nottingham';
```

---

## DELETE

The `DELETE` command removes rows from a table.

### Example

Delete the record for Smith:

```sql
DELETE FROM Customer
WHERE customerName = 'Smith';
```

### Deleting All Rows

If the `WHERE` clause is omitted, all rows are removed:

```sql
DELETE FROM Customer;
```

The table itself remains, but all data is deleted.

---

# COMMIT and ROLLBACK

DML commands change data within a transaction. These changes can either be saved permanently using `COMMIT` or undone using `ROLLBACK`.

## COMMIT

The `COMMIT` command permanently saves all changes made during the current transaction.

```sql
COMMIT;
```

Example:

```sql
INSERT INTO Customer(customerName, street, customerCity)
VALUES ('Jones', 'High Street', 'Derby');

COMMIT;
```

The new customer record is now permanently stored in the database.

---

## ROLLBACK

The `ROLLBACK` command undoes all changes made since the last commit.

```sql
ROLLBACK;
```

Example:

```sql
DELETE FROM Customer
WHERE customerName = 'Smith';

ROLLBACK;
```

The delete operation is cancelled and the row is restored.

### Example Transaction

```sql
INSERT INTO Customer(customerName, street, customerCity)
VALUES ('Brown', 'Queen Street', 'Nottingham');

UPDATE Customer
SET customerCity = 'Derby'
WHERE customerName = 'Smith';

ROLLBACK;
```

Neither change takes effect because the transaction was rolled back before being committed.

---

# System Tables (Data Dictionary Views)

Oracle stores information about database objects in special system tables known as **data dictionary views**.

These views contain information about tables, columns, constraints, indexes, users, and other database objects.

---

## USER_TABLES

`USER_TABLES` stores information about tables owned by the current user.

List all tables owned by the user:

```sql
SELECT table_name
FROM USER_TABLES;
```

---

## USER_TAB_COLUMNS

`USER_TAB_COLUMNS` stores information about table columns.

Display the columns and data types in the CUSTOMER table:

```sql
SELECT column_name, data_type
FROM USER_TAB_COLUMNS
WHERE table_name = 'CUSTOMER';
```

---

## USER_CONSTRAINTS

`USER_CONSTRAINTS` stores information about constraints such as primary keys, foreign keys and check constraints.

Display constraints on the CUSTOMER table:

```sql
SELECT constraint_name, constraint_type
FROM USER_CONSTRAINTS
WHERE table_name = 'CUSTOMER';
```

---

# Summary

| Command | Purpose |
|----------|---------|
| `INSERT` | Adds new rows to a table |
| `SELECT` | Retrieves data from a table |
| `UPDATE` | Modifies existing data |
| `DELETE` | Removes rows from a table |
| `COMMIT` | Permanently saves changes |
| `ROLLBACK` | Undoes changes since the last commit |

Data dictionary views such as `USER_TABLES`, `USER_TAB_COLUMNS`, and `USER_CONSTRAINTS` allow users to view information about the structure of their database objects.
