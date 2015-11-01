---
layout: post
title: "How to use MySQL"
description: ""
category: skills
tags: [How-To, MySQL]
---
{% include JB/setup %}

This is a How-To tutorial on MySQL. Everything here is very simple, but really helpful for beginners.

## How to Use MySQL

### Login

Open the terminal and type:

	mysql -h host -u username -p

If you work on local machine, simply type:

	mysql -u username -p

and type your password if you set one before or just press enter.

If you find ``>mysql`` appear, congratulations! You can type ``exit`` to exit.

### Create a database

We create a new database ``samp_db``

	create database congratulation;

Note: All MySQL command end with a semicolon(;), without which the command prompt will expect your further input.

You can check the existing databases by

	show databases;

You can select the database you want to work on, for example ``samp_db``, by

	use samp_db;

### Create a table

Here is an example I stole from [MySQL 21 minutes](http://wiki.jikexueyuan.com/project/mysql-21-minutes/)

	create table students
	（
	    id int unsigned not null auto_increment primary key,
	    name char(8) not null,
	    sex char(2) not null,
	    age tinyint unsigned not null,
	    tel char(13) null default "-"
	);

It may be stupid to type those line by line in command prompt. You can type them in any editor and save as ``createtable.sql``. Then simply

	mysql -D samp_db -u root -p < createtable.sql

Let's take a quick look on `` id int unsigned not null auto_increment primary key`` and see what happened.
* ``id`` is the name of this column
* ``int`` the data type of this column is integer (-2147483648~2147483647).  ``unsigned`` indicates this is a unsigned integer type.
* ``not null`` the data in this column must has a value. By default, data can be ``NULL``.
* ``auto_increment`` can only be used in integer array. If the new input value is ``NULL``, MySQL will fill in a number larger than existing stored number automatically. Only one key can has the property and it has to be ``primary key``.
* All values in ``primary key`` must be unique.

You check the existing tables by

	show tables;

You can see the detailed information of a table, for example ``students``, by

	describe students;


## How to Manipulate Data

### Insert new data to a table

We insert a new student with information of name, sex and age into the table ``students``.

	insert into students (name, sex, age) values("Mary", "F", 21);

If you like to input all the information of a new student, you can type

	insert into students values(NULL, "Jack", "M", 20, "13811371377");

### Retrieve information from a table

Print the telephone number information for students over 21.

	select tel from students where age>=21;

Print all the information in table.

	select * from students;

Print all the information for female with id smaller than 5.

	select * from students where sex="F" and id<5;

### Update data

Update the student with id=5 to default phone number.

	update students set tel=default where id=5;

Increase everyone's age by 1.

	update students set age=age+1;

### Delete data

Delete student with id=2.

	delete from students where id=2;

Delete all students over 21.

	delete from students where age>21;

Delete all.

	delete from students;

## How to Manipulate Table

### Add new column

Add address at the end.

	alter table students add address char(60);

Add birthday after age.

	alter table students add birthday after age;

### Change column

Rename tel to telephone.

	alter table students change tel telphone char(13) default "-";

### Drop column

Drop birthday.

	alter table students drop birthday;

### Rename table
Rename students as workmates.

	alter table students rename workmates;

## Drop table and database

### Drop the entire table

	drop table workmates;

### Drop the entire database

	drop database samp_db;

I hope this is useful.

---

Reference: [MySQL 21 minutes](http://wiki.jikexueyuan.com/project/mysql-21-minutes/)