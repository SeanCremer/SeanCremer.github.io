# Choosing a Primary Key


## Table of contents
1. [Introduction](#introduction)
2. [Some Fundamental Truths](#fundamentalTruths)
    1. [-What are some of the Gotchas](#gotachs)
3. [Some Simple Real World Realities](#realities)
    1. [-Integers](#integers)
    2. [-Dates](#dates)
    3. [-Strings](#strings)
    4. [-GUIDS](#guids)
4. [What are some of the big Questions](#questions)
    1. [-What is the Purpose of the Table](#purpose)
    2. [-What are teh Expected Transaction Volumes](#volumes)

<a name="introduction"></a>

## Introduction

Choosing the right Primary Key for a SQL table would seem to the laymen to be a very simple thing to do. In reality there are many things that you need to ask yourself about the data, the design as well as intended use.

Essentially the Primary key on a table is the mechanism through which SQL searches for the data you are looking for.  It has impact on anything you would want to do with the Table; inserting, updating, deleting or just plain joining to the table. 

For more information on the principals of Databse design you can refer to a previous post on [Introduction to Database Design](IntroductionToDatabaseDesign.md).

<a name="fundamentalTruths"></a>

## Some Fundamental Truths

There are some rules that govern creating primmary key values on SQL server tables.  These rules are based around the reality that a Primary Key is in actual fact a constraint


<a name="gotachs"></a>

### What are some of the Gotchas

- A Microsoft SQL Server Table can have only one Primary Key. (As they say in the movie Highlander, "There can e only one") 
- All columns that are added to a Primary Key cannot be nullable.  They wil be created not Nullable if you fail to specify that they are Not Nullable.
- If you did not realise it by now, it is by it very definition an Index that must have a unique value for each row in the table. If the chosen columns do not produce uniqueness, you cannot make it a Primmary Key. 

<a name="realities"></a>

## Some Simple Real World realities

Primary key columns can be any of the main SQL data types including strings. Each of the possible data types has consequences when chosen and implications when developing against them.  Cutting to the chase, just beacuse a partiicular data type can be made into a primary key does not mean it is a good idea. 

<a name="integers"></a>

### Integers

Integers are your friend.  If you are designing a new database you should as best as posible try and make all your Primary Keys integers. Internally under the hood SQL server is able to work with Integers faster than other data types in nearly every implmeted design. They allow for faster joins between tables, improved lookups and smaller Phsycial volume indexes which improves the performnce of the index itself.

<a name="dates"></a>

### Dates

I have unfortunately seen this in production quite often on various systems. Mostly on systems where people have called me to come and help them out with their database performance problems.  In a very simple like for like comparison an Integer is stored in 4 Bytes a DateTime in 8 bytes.  This naturally means you have doubled the size of reading volume for the index by using a date than would have been the case with an Integer. If your system is heavly transaction choosing a DateTime column for a Primary key is usually a done under the misguided belief that it would help out when writing reports that query the system on date ranges.

DateTime fileds are better suited to additional helper Indexes but not the Primary Key.  If you are adamant in your approach to wanting a date range searchable primary key then consider turning it into an Integer representation of the Date.  This can be something similar to interanl storage value which actually has very little meaning when visually seen or just make the date 2017-01-01  equal the Integer 20170101.  This will allow you to maintain your search options.  

Still at the very least in my experience it is not a good idea to use date,  I would strongly advise against it if you want a fast system.
 
<a name="strings"></a>

### Strings

Not as bad as dates but not as great as Integers. Problem is speed when SQL has to potetnially compare and search ever increasing String sizes.  I have often seen Char fields Storing Currency or Country ISOCodes being made into a Primary Key. A specified, specifc sized char field in those circumstances does not perform to badly on a table that does not have millions of rows. String Codes such as ISO Codes, Product Codes I would rather put a second index on them and hae a surrogate/Anonymous Integer as the Primary Key.

<a name="guids"></a>

### GUIDS

In the last few years I have seen more and more tables where a GUID/UniqueIdentifier is used as a Primay Key.  Each time I have to resist the urge to seek out and torture the individual responsible.  Then I remember that going to prison over somomes bad database design is not a very good use of my time.  Taking into account the same concept as why date is bad, a GUID in SQL is stored in 16 Bytes.  That is 4 times bigger than an Integer. I might in another post continue my rant on why I do not Like GUIDS as Primary Keys.  

I do believe GUIDs have a place but not in a Primary Key; stick to a Surrogate Integer Key. 

<a name="questions"></a>

## What are some of the Big Questions

When designing a table the are are a few questions that need to be answered to decide adequately what type of primary key you will need. These qusetions usually relate to the production nature of the talbe and how it will be accessed and used.

<a name="purpose"></a>

### What is the Purpose of the Table

The below are some of the more simple questions that can start pushing you into the right direction for a Primary Key Choice.

#### Is the table part of an OLTP system

OLTP systems have a variety of different table types.  

- Transactional
- Small Attribute Tables that foreign key to transactional tables
- Large Attribute Tables such as your Customers

The main focus on a transacitional table is to ensure that inserts are extremely fast. You are also trying to get as many rows stored on a data page as possible so you should try to not include too many columns. If the columns seem to be getting more and more consider breaking the table apart.

#### Is the Table part of a Warehouse
Data warehouses by definition are there for the purpose of reporting and data analysis. In most data warehouses, data retrieval trumps inserts. The choice of primary key should allow for well defined CLustered data lookups and reads that support aggregations of data in the logical representation of how people percieve the data to add value to their organisation. In may cases well planned compositer primary keys allow for good data retrieval of data when needed in specific groupings. It is important t note that the choice of primary key for teh Datawarehouse table can and in most cases, should be different to its original parent table in the OLTP database.  This is in most part because they have different needs with regards to Insert versus retrieval of data. It is important to note that factors such as pre-aggregated tables and report caching tools could also have an impact on whether or not you build your primary keys for insert or retrieval speeds.
#### Is the Table part of a data Mart
Many of the Data Marts that  have seen in the last few years are doubling as the actual data warehouse.  If that is the case in your current infrastructre then the choise of Primary Key should follow the same logical needs of the datawarehouse where data retrieval is prefered over inserts speeds.
#### Is the table part of a staging process
In my experience, staging databases share the needs of both insert and retrieval considerations. How you design is dependant largely on the volume of data that passes throygh the staging area and the amount of Aggregations that you are preparing. What is most important is hat you remember to move the data off the OLTP system into the staging area before begginning any aggregations.  So the initial table might be prepped for insert.  The aggregation query looses retrieval perfromance but then stores th aggragation into a structure designed for a Composite primary key that is good for retriving the data before its movement to a mart or warehose. 


## Disclaimer
This is my personal blog. The views expressed on these pages are mine alone and not those of my employer.

© 2017. All rights reserved.


