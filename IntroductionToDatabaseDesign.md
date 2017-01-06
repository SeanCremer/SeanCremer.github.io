# Introduction to Database Design


## Table of contents
1. [Introduction](#introduction)
	1. [-Overview](#overview)
    2. [-Scope](#scope)
    3. [-Target Audience](#targetaudience)
2. [Fundamental Terminology](#terminology)
    1. [-General Terminology](#generalterminology)

<a name="introduction"></a>

# Introduction

<a name="overview"></a>

### Overview

Far too few database developers in this day and age get the opportunity to learn how to design relation databases.  In most cases, they will on occasion be asked to add a few objects to an existing system while following the standards of the organisation.  Often these standards are suspect at best and are merely followed for conformity, convenience and to avoid making waves. 

These relatively infrequent changes do not hone the skills needed for effective design.  As such there is often a slow but continuous loss of overall good design principal over the life of the database.  Bolting changes on that really should have had more reflection before implementation only leads to one inevitable outcome.

In the world of Business applications the database can be described as the foundation to the system.   Clients can easily be rewritten or skinned differently.  Databases on the other hand carry across with them implications such as migrations, history and data volume which in all major modification scenarios often lead to downtime.  Taking that into account it is always a great surprise to me how the database design portion of the product often gets the shortest development cycle in the process.

If you have built a database that was designed to be a single story building, there is no way you can build a second story on top of it without ripping out the foundation that has already been laid.  To maintain database performance it is critical to understand that continuous unplanned additions done in an unplanned way jeopardise the future of the product.  It does not take a rocket scientist to know that no matter how awesome the house looks; if the foundation is faulty, trouble is only a few short CPU cycles around the corner.

This state of being is why it is even more important that the average DB developer be more prepared to produce better designs in the very restricted development windows that exist.

<a name="scope"></a>

### Scope

The purpose of this post is to present the basic introductory understandings and concepts that should be adhered to when designing database objects.  It is unavoidable with the subject matter to not require an understanding of basic key terminology.  That being said the onus is being left on the course attendees to investigate further if knowing the 100% definition of anything is an absolute must in their world.

I however, will attempt to convey the principals and necessary questions that should be asked when designing without getting bogged down with too much of the technicalities.  Knowing word for word definitions are not needed for good design if the principals of what is trying to be achieved are understood and followed.  Database design by its very nature is literally a cookie cutter implementation of the same principals over and over.  Follow them and your databases will have a long and sturdy future.

<a name="targetaudience"></a>

### Target Audience

A myriad of people will be able to benefit from understanding the principals of design that will be presented.

1. Naturally the benefit to people already responsible for design considerations at a database level will leverage the most from the course.
2. Client developers who want to have a look at the Dark side and see how the other side has to live and why they are often asked to do something completely daft and foreign.
3. Testers who wish to be able to provide useful feedback as to potential design flaws by understanding future caveats of new designs.
4. Support personnel who are interested in being able to interpret and understand the implications of what they are seeing from a design perspective.

<a name="terminology"></a>

# Fundamental Terminology

Most of the complex definitions in this section need not be learnt or understood 100 percent for good basic database designs to be made.  Knowing them and understanding them do allow for being able to interpret and comprehend the more advanced concepts in books and published papers on database design.  So for the more serious participant in this course, it would definitely be beneficial to spend a bit more time learning these concepts inside out!

<a name="generalterminology"></a>

## General Terminology

1. **Data Element** is an atomic unit of data that has precise meaning.  (Read up on Metadata for more understanding.  Often implanted in production with overloading which means there is multiple meanings to the single data element which breaks the conceptual understanding of a single precise meaning.  This is an extremely bad practice and now requires domain knowledge to interpret information.
2. **Data Domain** refers to all the values that might be contained in a Data Element.  In laymen terms the range of data that can be stored.  In most cases it is restricted by choosing a Data Type for a Column. 
3. **Entity** Loosely defined as a table.  Normally used in the Logical or Conceptual understanding of a Design. Definitions vary as the academics try to one up each other in how smart they are.  For our purposes an Entity is a table for design purposes.  When we define the final schema of the table then we refer to it as a table in its physical form.
4. **Row versus Record** Often used interchangeably but in reality Row refers to the actual data where each column represents a single piece of data, referred to in later publications as a tuple.  A Record on the other hand is usually used to describe the final resting place of the information in a file on Disk.  