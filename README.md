# Champions-Arena
A competitive programming platform.

## Commands for creation of MySQL tables:

```
CREATE DATABASE cparena;

USE cparena;


CREATE TABLE USER
(
uid varchar(40) PRIMARY KEY,
uname varchar(40),
passwd varchar(40),
college varchar(100),
rating int DEFAULT 1500
);


CREATE TABLE CONNECTION
(
user1 varchar(40) REFERENCES USER(uid),
user2 varchar(40) REFERENCES USER(uid),
status tinyint(4) DEFAULT 0
);


CREATE TABLE PROBLEM
(
ID varchar(10) PRIMARY KEY,
Title varchar(40) NOT NULL,
Statement varchar(1000),
Level int NOT NULL,
);


INSERT INTO PROBLEM VALUES('1A', 'Addition', 'For T test cases, add two numbers and print the result, each on a new line.', 700);

INSERT INTO PROBLEM VALUES('1B', 'Multiplication', 'For T test cases, multiply two numbers and print the result, each on a new line.', 800);


CREATE TABLE TESTCASES
(
ID varchar(10) REFERENCES PROBLEM(ID),
Input varchar(10000),
ExpectedOutput varchar(10000)
);


INSERT INTO TESTCASES VALUES('1A', 1, '3\n0 1\n2 3\n100 200\n', '1\n5\n300\n');

INSERT INTO TESTCASES VALUES('1A', 2, '5\n0 0\n10000 10000\n-9 -16\n25 -25\n99999 1\n', '0\n20000\n-25\n0\n100000\n');

INSERT INTO TESTCASES VALUES('1B', 1, '3\n0 1\n2 3\n100 200\n', '0\n6\n20000\n');

INSERT INTO TESTCASES VALUES('1B', 2, '5\n0 0\n100 100\n-9 -16\n25 -25\n99999 1\n', '0\n10000\n144\n-625\n99999\n');
```
