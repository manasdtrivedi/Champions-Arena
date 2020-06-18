# Champions Arena
The project 'Champions Arena' is a competitive programming platform, which supports systems running on Linux.

Champions_Arena.jar is the executable file to be run, which is present at Champions Arena/dist.

To run this file, first check if Java is installed on your system by issuing the following command in the Terminal:
```
java -version
```

If Java is not present, issue this command:
```
sudo apt install default-jre
```

This downloads the Java Runtime Environment. Now, in MySQL, issue the following commands:
```
CREATE DATABASE ChampionsArena;

USE ChampionsArena;


CREATE TABLE USER
(
uid varchar(40) PRIMARY KEY,
uname varchar(40),
passwd varchar(40),
college varchar(100)
);


CREATE TABLE CONNECTION
(
user1 varchar(40),
user2 varchar(40),
status tinyint(4) DEFAULT 0,
FOREIGN KEY(user1) REFERENCES USER(uid),
FOREIGN KEY(user2) REFERENCES USER(uid)
);


CREATE TABLE CONTEST
(
ID varchar(10) PRIMARY KEY,
Name varchar(50) NOT NULL,
Start datetime,
End datetime
);


INSERT INTO CONTEST VALUES('R1', 'Round 1', '2020-03-15 15:00:00', '2020-03-31 15:00:00');

INSERT INTO CONTEST VALUES('R2', 'Round 2', '2020-06-01 17:30:00', '2020-07-20 17:30:00');


CREATE TABLE PROBLEM
(
ID varchar(10) PRIMARY KEY,
Title varchar(40) NOT NULL,
Statement varchar(1000),
Level int NOT NULL,
ContestID varchar(10),
FOREIGN KEY(ContestID) REFERENCES CONTEST(ID)
);


INSERT INTO PROBLEM VALUES('1A', 'Addition', 'For T test cases, add two numbers and print the result, each on a new line.', 700, 'R1');

INSERT INTO PROBLEM VALUES('1B', 'Multiplication', 'For T test cases, multiply two numbers and print the result, each on a new line.', 800, 'R1');

INSERT INTO PROBLEM VALUES('1C', 'Remainder', 'For T test cases, find the remainder when the first number is divided by the second, and print the result, each on a new line', 800, 'R1');

INSERT INTO PROBLEM VALUES('2A', 'Subtraction', 'For T test cases, subtract the second number from the first, and print the result, each on a new line', 700, 'R2');

INSERT INTO PROBLEM VALUES('2B', 'Division', 'For T test cases, divide the first number by the second, and print the result, each on a new line', 800, 'R2');

INSERT INTO PROBLEM VALUES('2C', 'Prime Numbers', 'For T test cases, print YES if input number is prime, and NO otherwise. Print each answer on a new line', 1200, 'R2');


CREATE TABLE TESTCASE
(
ID varchar(10),
TestNo int,
Input varchar(10000),
ExpectedOutput varchar(10000),
FOREIGN KEY(ID) REFERENCES PROBLEM(ID)
);


INSERT INTO TESTCASE VALUES('1A', 1, '3\n0 1\n2 3\n100 200\n', '1\n5\n300\n');

INSERT INTO TESTCASE VALUES('1A', 2, '5\n0 0\n10000 10000\n-9 -16\n25 -25\n99999 1\n', '0\n20000\n-25\n0\n100000\n');

INSERT INTO TESTCASE VALUES('1B', 1, '3\n0 1\n2 3\n100 200\n', '0\n6\n20000\n');

INSERT INTO TESTCASE VALUES('1B', 2, '5\n0 0\n100 100\n-9 -16\n25 -25\n99999 1\n', '0\n10000\n144\n-625\n99999\n');

INSERT INTO TESTCASE VALUES('1C', 1, '3\n10 5\n101 3\n5 4\n', '0\n2\n1\n');

INSERT INTO TESTCASE VALUES('1C', 2, '3\n29 10\n5 1000\n0 1\n', '9\n5\n0\n');

INSERT INTO TESTCASE VALUES('2A', 1, '3\n0 0\n25 16\n16 25\n', '0\n9\n-9\n');

INSERT INTO TESTCASE VALUES('2A', 2, '1\n1 -1\n', '2\n');

INSERT INTO TESTCASE VALUES('2B', 1, '1\n5 2\n', '2\n');

INSERT INTO TESTCASE VALUES('2B', 2, '3\n10 5\n101 3\n0 1\n', '2\n33\n0\n');

INSERT INTO TESTCASE VALUES('2C', 1, '5\n2\n3\n4\n5\n', 'YES\nYES\nNO\nYES\n');

INSERT INTO TESTCASE VALUES('2C', 2, '5\n23\n29\n44\n55\n', 'YES\nYES\nNO\nNO\n');


CREATE TABLE SUBMISSION
(
uid varchar(40),
ContestID varchar(10),
A tinyint(4),
B tinyint(4),
C tinyint(4),
PRIMARY KEY(uid, ContestID),
FOREIGN KEY(uid) REFERENCES USER(uid),
FOREIGN KEY(ContestID) REFERENCES CONTEST(ID)
);
```

Next, ensure that your MySQL 'Root' password is set to "" i.e. empty.

Now, double-click Champions_Arena.jar to run it. If it doesn't run, right click it, go to Properties, and under the Permissions tab tick the 'Allow executing file as program' checkbox.

### Team Members
```
Aditya Chandrashekhar Sohoni    (181CO203)
Manas Trivedi                   (181CO231)
```
