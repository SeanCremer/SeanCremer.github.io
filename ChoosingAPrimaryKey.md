# Choosing a Primary Key


## Table of contents
1. [Introduction](#introduction)
2. [Some Fundamental Truths](#fundamentalTruths)
    1. [-What are some of the Gotchas](#gotachs)
3. [Some Simple Real World Realities](#realities
    1. [-Integers](#integers)
    2. [-Dates](#dates)
    3. [-Strings](#strings)
    4. [-GUIDS](#guids)

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

Primary key columns can be any of the main SQL data types including strings. Each of the possible data types has consequences when chosen and implications when developing against them.  Cutting to the chase just beacuse a partiicular data type can be made into a primary key does not mean it is a good idea. 

<a name="integers"></a>

### Integers

<a name="dates"></a>

### Dates

<a name="strings"></a

### Strings

<a name="guids"></a>

### GUIDS


## Disclaimer
This is my personal blog. The views expressed on these pages are mine alone and not those of my employer.

© 2017. All rights reserved.


