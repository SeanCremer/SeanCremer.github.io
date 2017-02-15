
## Doomed, We Are all Doomed, by Niels Berglund (2017-02-15)

Niels Berglund is a colleague of mine as well as the gent that he was arguing with in his post, namely Sameer Chunilall.  I regard both as some of the best people to go to when you need to know something about SQL Server. 

On the Topic of **XACT_ABORT ON**, my feelings tend to flow in the same direction as Niels.  Not to say that I don't think going down the road of building a completely new database planned around the use of XACT_ABORT is a bad thing.  In that circumstance where you control your complete call stack and understand the implications it can be used for good rather than evil. However in a very old system with decadeds of SQL code using every potential form of error handling and when procedures call down into each other in the double figure count; adding a random **XACT_ABORT ON** can cause more problems than what you were trying to solve.

Despite all of that the link below is to one of my favourite blog posts by Niles about doomed transactions, well worth a read!!

[Doomed, We are All Doomed I Say! by Niels Berglund](http://www.nielsberglund.com/2017/01/27/doomed-we-are-all-doomed/)


## Introduction to Choosing a Primary Key

Choosing the right Primary Key for a SQL table would seem to the laymen to be a very simple thing to do. In reality there are many things that you need to ask yourself about the data, the design as well as intended use.
Essentially the Primary key on a table is the mechanism through which SQL searches for the data you are looking for. It has impact on anything you would want to do with the Table; inserting, updating, deleting or just plain joining to the table.

[Read More...](ChoosingAPrimaryKey.md)

## Top Developer Tools for 2016 (2017-01-25)

Nice read to see how the different products are gaining ground while others are loosing.  Good opportunity to highlight a prodcut you never knew about that could be helpfull.

[Read More ...](https://stackshare.io/posts/top-developer-tools-2016)

Nice one StackShare!

## Introduction to Database Design (2017-01-09)
Far too few database developers in this day and age get the opportunity to learn how to design relation databases.  In most cases, they will on occasion be asked to add a few objects to an existing system while following the standards of the organisation.  Often these standards are suspect at best and are merely followed for conformity, convenience and to avoid making waves. 

These relatively infrequent changes do not hone the skills needed for effective design.  As such there is often a slow but continuous loss of overall good design principal over the life of the database.  Bolting changes on that really should have had more reflection before implementation only leads to one inevitable outcome.

In the world of Business applications the database can be described as the foundation to the system.   Clients can easily be rewritten or skinned differently.  Databases on the other hand carry across with them implications such as migrations, history and data volume which in all major modification scenarios often lead to downtime.  Taking that into account it is always a great surprise to me how the database design portion of the product often gets the shortest development cycle in the process.

If you have built a database that was designed to be a single story building, there is no way you can build a second story on top of it without ripping out the foundation that has already been laid.  To maintain database performance it is critical to understand that continuous unplanned additions done in an unplanned way jeopardise the future of the product.  It does not take a rocket scientist to know that no matter how awesome the house looks; if the foundation is faulty, trouble is only a few short CPU cycles around the corner.

This state of being is why it is even more important that the average DB developer be more prepared to produce better designs in the very restricted development windows that exist.
 
[Read More...](IntroductionToDatabaseDesign.md)

## Disclaimer
This is my personal blog. The views expressed on these pages are mine alone and not those of my employer.

© 2017. All rights reserved.


