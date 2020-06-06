# Champions-Arena
A competitive programming platform.

### Commands for creation of MySQL tables:

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
ContestID varchar(10) REFERENCES CONTEST(ID)
);


INSERT INTO PROBLEM VALUES('1A', 'Addition', 'For T test cases, add two numbers and print the result, each on a new line.', 700);

INSERT INTO PROBLEM VALUES('1B', 'Multiplication', 'For T test cases, multiply two numbers and print the result, each on a new line.', 800);

INSERT INTO PROBLEM VALUES('2A', 'Subtraction', 'For T test cases, subtract the second number from the first, and print the result, each on a new line', 700, 'R2');

INSERT INTO PROBLEM VALUES('2B', 'Division', 'For T test cases, divide the first number by the second, and print the result, each on a new line', 800, 'R2');

INSERT INTO PROBLEM VALUES('3A', 'Remainder', 'For T test cases, find the remainder when the first number is divided by the second, and print the result, each on a new line', 800, 'R3');

INSERT INTO PROBLEM VALUES('3B', 'Prime Numbers', 'For T test cases, print YES if input number is prime, and NO otherwise. Print each answer on a new line', 1200, 'R3');


CREATE TABLE TESTCASE
(
ID varchar(10) REFERENCES PROBLEM(ID),
Input varchar(10000),
ExpectedOutput varchar(10000)
);


INSERT INTO TESTCASES VALUES('1A', 1, '3\n0 1\n2 3\n100 200\n', '1\n5\n300\n');

INSERT INTO TESTCASES VALUES('1A', 2, '5\n0 0\n10000 10000\n-9 -16\n25 -25\n99999 1\n', '0\n20000\n-25\n0\n100000\n');

INSERT INTO TESTCASES VALUES('1B', 1, '3\n0 1\n2 3\n100 200\n', '0\n6\n20000\n');

INSERT INTO TESTCASES VALUES('1B', 2, '5\n0 0\n100 100\n-9 -16\n25 -25\n99999 1\n', '0\n10000\n144\n-625\n99999\n');

INSERT INTO TESTCASE VALUES('2A', 1, '3\n0 0\n25 16\n16 25\n', '0\n9\n-9\n');

INSERT INTO TESTCASE VALUES('2A', 2, '1\n1 -1\n', '2\n');

INSERT INTO TESTCASE VALUES('2B', 1, '1\n5 2\n', '2\n');

INSERT INTO TESTCASE VALUES('2B', 2, '3\n10 5\n101 3\n0 1\n', '2\n33\n0\n');

INSERT INTO TESTCASE VALUES('3A', 1, '3\n10 5\n101 3\n5 4\n', '0\n2\n1\n');

INSERT INTO TESTCASE VALUES('3A', 2, '3\n29 10\n5 1000\n0 1\n', '9\n5\n0\n');

INSERT INTO TESTCASE VALUES('3B', 1, '5\n2\n3\n4\n5\n', 'YES\nYES\nNO\nYES\n');

INSERT INTO TESTCASE VALUES('3B', 2, '5\n23\n29\n44\n55\n', 'YES\nYES\nNO\nNO\n');
```
