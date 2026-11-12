**Relation Tables**

attribute = columns

Tuples = rows

All cells contain single data values



**Data Types:** 

Character(6) or char(6) is for words.

VARCHAR(6) is more memory efficient

Integer or Int e.g 12

Decimal(5,3) or numeric (5,3) stores values such as 12.345

FLOAT, REAL stores decimal but doesn't have set precision

DATE stores Dates and times



**Creating Tables**



CREATE TABLE Tutor ( 

&#x09;name VARCHAR(20) PRIMARY KEY,

&#x09;roomNo INT);



**Primary Key** is a set of columns that together makes each row have distinct set of column values 



**DROP TABLE:** this command allows the removal of the database components



**Constraints** - a rule that restricts the values in databases.



name CHAR(20) CONSTRAINT stName RERFENCES tutor,



**Composite Primary Keys** are where two columns are the primary key



CREATE TABLE lecture (

&#x09;name CHAR(20),

&#x09;roomNo INT,

&#x09;occurs DATE,

&#x09;lecturer VARCHAR(20),

&#x09;PRIMARY KEY (occurs, roomNo)

&#x09;);



**Unique, Not Null, check, default, Constraints**

The gender column can only have the values M or F or U and U as a default value.

example:



CREATE TABLE PERSON(

&#x09;name VARCHAR(10),

&#x09;gender CHAR(1) DEFAULT 'U'

&#x09;	CHECK(gender IN ('M','F','U')



If you insert a new row, the name will be NULL, and it will default to U if it is null.

INSERT INTO Person (name) VALUES ('Smith')



**Foreign Keys** this is an inter relational constraint in which row values are set of table columns in one table B can only occyr if they match the row values in a set of columns in another value or these values are NULL.



if b reference A, A must exist



if a row with a foreign key is updated or deleted the referential constraint can stop the change.



it can be set null, set default

CONSTRAINT stLec

&#x09;FOREIGN KEY (LectureNO, occurs)

&#x09;REFERENCES Lecture(lectureNo, occurs)

&#x09;ON DELETE SET NULL



**Altering a Foreign Key**

ALTER TABLE student DROP PRIMARY KEY;

ALTER TABLE student ADD CONSTRAINT

stLec FOREIGN KEY (roomNo,occurs)

REFERENCES Lectures(roomNo, occurs) ON DELETE CASCADE



**Displaying table info**

Desc table customer



