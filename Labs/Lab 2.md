Inserting data into the branch table
```SQL
INSERT INTO Branch (branchName, assets, branchCity)
VALUES ('Yorkshire', 10000.00, 'Nottingham');

INSERT INTO Branch (branchName, assets, branchCity)
VALUES ('Midlands', 20000.00, 'Nottingham');

INSERT INTO Branch (branchName, assets, branchCity)
VALUES ('RoyalBank', 25000.00, 'Nottingham');

INSERT INTO Branch (branchName, assets, branchCity)
VALUES ('HFE', 15000.00, 'Derby');

INSERT INTO Branch (branchName, assets, branchCity)
VALUES ('Southern', 30000.00, 'Derby');
```
Inserting data into customer table
```SQL
INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Jones', 'Victoria', 'Nottingham');

INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Patel', 'Church', 'Nottingham');

INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Smith', 'Derby', 'Leicester');

INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Ahmed', 'Church', 'Derby');

INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Braun', 'Alfred', 'Derby');

INSERT INTO Customer (customerName, street, customerCity)
VALUES ('Chan', 'Victoria', 'Nottingham');
```
Inserting Data into the deposit table
```SQL
INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Jones', 'Yorkshire', 1, 100.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Braun', 'Midlands', 20, 150.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Ahmed', 'RoyalBank', 30, 480.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Smith', 'Midlands', 21, 600.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Patel', 'RoyalBank', 31, 450.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Patel', 'Midlands', 22, 70.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Braun', 'Southern', 41, 2000.00);

INSERT INTO Deposit (customerName, branchName, accountNumber, balance)
VALUES ('Jones', 'HFE', 42, 4100.00);
```
Inserting data into the Loan table 
```SQL
INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Jones', 'Yorkshire', 11, 3000.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Chan', 'Yorkshire', 12, 2500.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Ahmed', 'Yorkshire', 13, 1800.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Smith', 'Midlands', 50, 5000.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Smith', 'RoyalBank', 6, 500.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Patel', 'Midlands', 51, 1000.00);

INSERT INTO Loan (customerName, branchName, loanNumber, amount)
VALUES ('Jones', 'Midlands', 61, 2000.00);
```

Checking the data has been inserted into the table properly
```SQL
SELECT * FROM Customer;
SELECT * FROM Loan;
SELECT * FROM Deposit
SELECT * FROM Branch;

COMMIT;
```
This saved the data and checked that it was inserted properly

Update the customer balance with 10% interest in the deposit table with the branch name 'RoyalBank' rollbacl changes once checking answer
```Sql
UPDATE Deposit SET balance = balance * 1.1
WHERE branchName = 'RoyalBanl';

SELECT * FROM Deposit;
ROLLBACK;
```
Delete the loans that have an amount over 2000,00 then rollback the changes after 
```SQL
DELETE FROM loan
WHERE amount >2000;

SELECT * FROM Loan;
ROLLBACK;

```
