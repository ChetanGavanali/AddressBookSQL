# AddressBookSQL

UC1

 create database address_book;

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| address_book       |
| information_schema |
| mysql              |
| payroll_service    |
| performance_schema |
+--------------------+

_________________________________________________________________________________________________________________________________________________________________

UC2

mysql> use address_book;
Database changed
mysql> create table address_book
    -> (
    -> firstname    VARCHAR(20) NOT NULL,
    -> lastname     VARCHAR(20) NOT NULL,
    -> address      VARCHAR(100) NOT NULL,
    -> city         VARCHAR(20) NOT NULL,
    -> state        VARCHAR(20) NOT NULL,
    -> zip          LONG NOT NULL,
    -> phonenumber  LONG NOT NULL,
    -> email        VARCHAR(50) NOT NULL
    -> );


mysql> describe address_book;
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| firstname   | varchar(20)  | NO   |     | NULL    |       |
| lastname    | varchar(20)  | NO   |     | NULL    |       |
| address     | varchar(100) | NO   |     | NULL    |       |
| city        | varchar(20)  | NO   |     | NULL    |       |
| state       | varchar(20)  | NO   |     | NULL    |       |
| zip         | mediumtext   | NO   |     | NULL    |       |
| phonenumber | mediumtext   | NO   |     | NULL    |       |
| email       | varchar(50)  | NO   |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+

________________________________________________________________________________________________________________________________________________________________

UC3

mysql> insert into address_book (firstname, lastname, address, city, state, zip, phonenumber, email) values
    -> ('Chetan','Gavanali','Mutaga','Belgaum','Karnataka','591124','9449441490','chetangavanali@gmail.com'),
    -> ('Prakash','Doni','BTM','Banglore','Karnataka','590001','9060509703','jpdoni@gmail.com'),
    -> ('Ankush','Nagamoti','Powai','Mumbai','Maharashtra','123456','9481409598','ankushnagamoti@gmail.com');


mysql> select * from address_book;
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+
| firstname | lastname | address | city     | state       | zip    | phonenumber | email                    |
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+
| Chetan    | Gavanali | Mutaga  | Belgaum  | Karnataka   | 591124 | 9449441490  | chetangavanali@gmail.com |
| Prakash   | Doni     | BTM     | Banglore | Karnataka   | 590001 | 9060509703  | jpdoni@gmail.com         |
| Ankush    | Nagamoti | Powai   | Mumbai   | Maharashtra | 123456 | 9481409598  | ankushnagamoti@gmail.com |
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+


___________________________________________________________________________________________________________________________________________________________________



UC4

mysql> update address_book set zip = 654321 where firstname='Ankush';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from address_book;
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+
| firstname | lastname | address | city     | state       | zip    | phonenumber | email                    |
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+
| Chetan    | Gavanali | Mutaga  | Belgaum  | Karnataka   | 591124 | 9449441490  | chetangavanali@gmail.com |
| Prakash   | Doni     | BTM     | Banglore | Karnataka   | 590001 | 9060509703  | jpdoni@gmail.com         |
| Ankush    | Nagamoti | Powai   | Mumbai   | Maharashtra | 654321 | 9481409598  | ankushnagamoti@gmail.com |
+-----------+----------+---------+----------+-------------+--------+-------------+--------------------------+

__________________________________________________________________________________________________________________________________________________________________

UC5


mysql> delete from address_book where firstname='Ankush';
Query OK, 1 row affected (0.01 sec)

mysql> select * from address_book;
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+
| firstname | lastname | address | city     | state     | zip    | phonenumber | email                    |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+
| Chetan    | Gavanali | Mutaga  | Belgaum  | Karnataka | 591124 | 9449441490  | chetangavanali@gmail.com |
| Prakash   | Doni     | BTM     | Banglore | Karnataka | 590001 | 9060509703  | jpdoni@gmail.com         |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+

___________________________________________________________________________________________________________________________________________________________________

UC6


mysql> select * from address_book where city='Banglore' or state='Karnataka';
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+
| firstname | lastname | address | city     | state     | zip    | phonenumber | email                    |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+
| Chetan    | Gavanali | Mutaga  | Belgaum  | Karnataka | 591124 | 9449441490  | chetangavanali@gmail.com |
| Prakash   | Doni     | BTM     | Banglore | Karnataka | 590001 | 9060509703  | jpdoni@gmail.com         |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+

____________________________________________________________________________________________________________________________________________________________________

UC7

mysql> select count(city) from address_book;
+-------------+
| count(city) |
+-------------+
|           2 |
+-------------+
1 row in set (0.01 sec)

mysql> select count(state) from address_book;
+--------------+
| count(state) |
+--------------+
|            2 |
+--------------+

___________________________________________________________________________________________________________________________________________________________________


UC8


mysql> select * from address_book where city='Belgaum' order by firstname;
+-----------+----------+---------+---------+-----------+--------+-------------+--------------------------+
| firstname | lastname | address | city    | state     | zip    | phonenumber | email                    |
+-----------+----------+---------+---------+-----------+--------+-------------+--------------------------+
| Chetan    | Gavanali | Mutaga  | Belgaum | Karnataka | 591124 | 9449441490  | chetangavanali@gmail.com |
+-----------+----------+---------+---------+-----------+--------+-------------+--------------------------+

____________________________________________________________________________________________________________________________________________________________________

UC9


mysql> alter table address_book add type VARCHAR(20) NOT NULL;
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> update address_book set type='Friend' where firstname='Mahantesh';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> update address_book set type='Family' where firstname='Ashok';
Query OK, 0 rows affected (0.00 sec)
Rows matched: 0  Changed: 0  Warnings: 0

mysql> select * from address_book;
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+------+
| firstname | lastname | address | city     | state     | zip    | phonenumber | email                    | type |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+------+
| Chetan    | Gavanali | Mutaga  | Belgaum  | Karnataka | 591124 | 9449441490  | chetangavanali@gmail.com |      |
| Prakash   | Doni     | BTM     | Banglore | Karnataka | 590001 | 9060509703  | jpdoni@gmail.com         |      |
+-----------+----------+---------+----------+-----------+--------+-------------+--------------------------+------+

_____________________________________________________________________________________________________________________________________________________________________

UC10


mysql> select count(type) from address_book where type = 'friend';
+-------------+
| count(type) |
+-------------+
|           0 |
+-------------+

UC11


mysql> insert into address_book (firstname,lastname,address,city,state,zip,phonenumber,email,type) values
    -> ('Mahantesh','Patil','Vasant Vihar','Delhi','NewDelhi','111000','9740914617','mahanteshpatil@gmail.com','friend'),
    -> ('Ashok','Gavanali','Mutaga','Belgaum','Karnataka','591124','9731610440','ashokgavanali@gmail.com','family');
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select * from address_book;
+-----------+----------+--------------+----------+-----------+--------+-------------+--------------------------+--------+
| firstname | lastname | address      | city     | state     | zip    | phonenumber | email                    | type   |
+-----------+----------+--------------+----------+-----------+--------+-------------+--------------------------+--------+
| Chetan    | Gavanali | Mutaga       | Belgaum  | Karnataka | 591124 | 9449441490  | chetangavanali@gmail.com |        |
| Prakash   | Doni     | BTM          | Banglore | Karnataka | 590001 | 9060509703  | jpdoni@gmail.com         |        |
| Mahantesh | Patil    | Vasant Vihar | Delhi    | NewDelhi  | 111000 | 9740914617  | mahanteshpatil@gmail.com | friend |
| Ashok     | Gavanali | Mutaga       | Belgaum  | Karnataka | 591124 | 9731610440  | ashokgavanali@gmail.com  | family |
+-----------+----------+--------------+----------+-----------+--------+-------------+--------------------------+--------+
