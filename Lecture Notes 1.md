# Relational Tables

- **Attributes** = Columns
- **Tuples** = Rows
- Each cell contains a single data value.

---

# Data Types

| Data Type | Description | Example |
|------------|-------------|---------|
| `CHAR(6)` | Fixed-length character string | `"London"` |
| `VARCHAR(6)` | Variable-length character string (more memory efficient) | `"London"` |
| `INT` / `INTEGER` | Whole numbers | `12` |
| `DECIMAL(5,3)` / `NUMERIC(5,3)` | Fixed precision decimal values | `12.345` |
| `FLOAT`, `REAL` | Decimal values without fixed precision | `12.34567` |
| `DATE` | Stores dates and times | `20-NOV-2025` |

---

# Creating Tables

```sql
CREATE TABLE Tutor (
    name VARCHAR(20) PRIMARY KEY,
    roomNo INT
);
```

## Primary Key

A **primary key** is a column, or set of columns, whose values uniquely identify each row in a table.

---

# Dropping Tables

The `DROP TABLE` command removes a table from the database.

```sql
DROP TABLE Tutor;
```

---

# Constraints

A **constraint** is a rule that restricts the values that can be stored in a database.

Example:

```sql
name CHAR(20) CONSTRAINT stName REFERENCES Tutor(name)
```

---

# Composite Primary Keys

A **composite primary key** consists of two or more columns that together uniquely identify a row.

```sql
CREATE TABLE Lecture (
    name CHAR(20),
    roomNo INT,
    occurs DATE,
    lecturer VARCHAR(20),
    PRIMARY KEY (occurs, roomNo)
);
```

---

# UNIQUE, NOT NULL, CHECK and DEFAULT Constraints

The `gender` column can only contain `M`, `F`, or `U`. If no value is provided, it defaults to `U`.

```sql
CREATE TABLE Person (
    name VARCHAR(10),
    gender CHAR(1) DEFAULT 'U'
        CHECK (gender IN ('M', 'F', 'U'))
);
```

Example insertion:

```sql
INSERT INTO Person (name)
VALUES ('Smith');
```

Result:

- `name` = `'Smith'`
- `gender` = `'U'` (default value)

---

# Foreign Keys

A **foreign key** is a constraint that ensures values in one table match values in another table.

If table **B** references table **A**, the referenced row in **A** must already exist (unless the foreign key value is `NULL`).

When a referenced row is updated or deleted, the foreign key constraint can:

- Prevent the change
- Set the foreign key to `NULL`
- Set the foreign key to a default value
- Cascade the change to dependent rows

Example:

```sql
CONSTRAINT stLec
    FOREIGN KEY (lectureNo, occurs)
    REFERENCES Lecture(lectureNo, occurs)
    ON DELETE SET NULL
```

---

# Altering Foreign Keys

Removing an existing primary key:

```sql
ALTER TABLE Student
DROP PRIMARY KEY;
```

Adding a foreign key constraint:

```sql
ALTER TABLE Student
ADD CONSTRAINT stLec
    FOREIGN KEY (roomNo, occurs)
    REFERENCES Lectures(roomNo, occurs)
    ON DELETE CASCADE;
```

`ON DELETE CASCADE` automatically removes dependent rows when the referenced row is deleted.

---

# Displaying Table Information

```sql
DESC Customer;
```

Displays the structure of the `Customer` table, including column names, data types, and constraints.


