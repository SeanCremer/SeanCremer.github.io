# Dynamic Management Objects (AKA DMVs)

## Table of contents
1. [Introduction](#introduction)
2. [MSSQL Meta data History](#history)
    1. [-Early Meta Data](#earlymetadata)
    2. [-MSSQL 2005 and Beyond](#beyond)

<a name="introduction"></a>

## Introduction

In my experience I have never met a real coder who did not want to know more about what was actually going on under the hood of tools and prodcuts that they work with. In the world of Microsoft SQL server getting more metadata has always been something that I have had a great appreciation for.

IN SQL 2005 Dynamic Management Objets (DMOs) were added.  This exposed a whole new world of possibilities. As the versions of MSSQL rolled out so did more DMOs. When working with developers I am often astonished by the notion that they believe that DMOs are there to add value to a DBAs life.  This confuses me immensely as a database developer should be paying attention to a whole bunch more than just indenting their SELECT statements when delivering complex solutions into complex environments.  DMOs provide information that can often change your approach to what you would do in certain situation before you productionise code.  Allowing for better knowledge of the working interplay of an existing system before you introduce something new to it.  Finding out what is happenign under the hood can change direction, thought and strategy with a few simple  SELECT statemetns from some awesome meta data providers, namely DMOs

This post will have quite a few parts continally added to it over the coming weeks to ensure exposure to all the wonders that DMOs provide.  If right now you have no idea what I am talking about with DMOs you probably one of the people that erroneously reference them as DMVs.  I will expalin the differences and eveolution of meta data as whole shortly.

<a name="history"></a>

## MSSQL Meta Data History

Depending on how long you have worked with MSSQL server you will hae been exposed to many different iterations of attempts at providing meta data.

<a name="earlymetadata"></a>

### Early Meta Data 

Prior to SQL 2005 meta data was provided by physucal system tables that existed in the Master DB.  The advent of tehse tables revolusionised debuggin within MSSQL. If you remember the good old **Sysobjects and Sysprocesses Tables** you are probably starting to get on in years.

Unfortunately their was no guarantee if you used these in production that they would stay the same from release to release.  Thankfully Microsoft realised the importance and value they added and CrCreated what we now know as **Compatibility Views**. These veiws were added for backward compatibility and proveide essentially teh same view of information .

<a name="beyond"></a>

### MSSQL 2005 and Beyond

With the Additiona of DMOs, also came Catalog Views.  The catalog views provided similar information to the compatibility view but with a keen eye to adding standards and conformity to other views.  Compare what comes back between the compatibilty **sys.sysobjets** versus the catalog view **sys.objects** to notice the differences.  At teh same time many of teh Catalog views actuall had Dynamic Mangement views which supreceded them.

As time has marched on in MSSQL and it versions so has teh avaialbility of DMO's to provide more and more metadata.  If you are interested in seeing what is avaialble on your sytem just run the following:

```sql
-- Produce a list of available Dynamic Management Views and Functions

SELECT  name ,         
        CASE type           
          WHEN 'V' THEN 'DMV'           
          WHEN 'IF' THEN 'DMF'         
        END AS DMO_Type
FROM master.sys.sysobjects
WHERE name LIKE 'dm_%' 
ORDER BY name;

```
 