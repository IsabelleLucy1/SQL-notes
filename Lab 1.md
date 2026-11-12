Creating Customer Table
```SQL
CREATE TABLE Customer(
customerName  VARCHAR(20) PRIMARY KEY,
street VARCHAR(20)
customerCITY VARCHAR(20)
);
```
Creating branch Table
```SQL
CREATE TABLE Branch(
branchName VARCHAR(20) PRIMARY KEY,
branchCity VARCHAR(20),
Assets DECIMAL(10,2) DEFAULT 0.00,
);
```
Altering the foreign keys 
```SQL
ALTER TABLE Deposit DROP CONSTRAINT DepToCust;
ALTER TABLE Deposit ADD CONSTRAINT DepToCust FOREIGN KEY
(customerName) REFERENCES Customer(customerName) ON DELETE
CASCADE;
```
Creating the deposit table
```SQL
CREATE TABLE Deposit (
customerName VARCHAR(20) CONSTRAINT DepToCust REFERENCES
Customer(customerName) ON DELETE CASCADE,
branchName VARCHAR(20) CONSTRAINT DepToBr REFERENCES
Branch(branchName) ON DELETE CASCADE,
accountNumber INTEGER PRIMARY KEY,
balance DECIMAL(10,2) DEFAULT 0.00
) ;
```
Creating loan table
```SQL
CREATE TABLE Loan (
customerName VARCHAR(20) CONSTRAINT LoanToCust REFERENCES
Customer(customerName) ON DELETE CASCADE,
branchName VARCHAR(20) CONSTRAINT LoanToBr REFERENCES
Branch(branchName) ON DELETE CASCADE,
loanNumber INTEGER PRIMARY KEY,
amount DECIMAL(10,2) DEFAULT 0.00
```

 

