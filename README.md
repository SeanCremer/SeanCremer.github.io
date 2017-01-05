# Welcome to MSSQL Playpen

As the name suggests, MSSQL Playpen is a place to present concepts and ideas around working with Microsoft SQL Server in a fun way.  Some topics covered will be extremely complex while others very introductory.  Most of the topics covered will be realted to my experiences over the years and hopefully some of them will be usefull to others.

That being said thre is no reason why we will not include anything of interest on the IT front.  Sugestions for topics can be sent to <SeanACremer@Gmail.com>


## Introduction to Database Design
Far too few database developers in this day and age get the opportunity to learn how to design relation databases.  In most cases, they will on occasion be asked to add a few objects to an existing system while following the standards of the organisation.  Often these standards are suspect at best and are merely followed for conformity, convenience and to avoid making waves. 

These relatively infrequent changes do not hone the skills needed for effective design.  As such there is often a slow but continuous loss of overall good design principal over the life of the database.  Bolting changes on that really should have had more reflection before implementation only leads to one inevitable outcome.

In the world of Business applications the database can be described as the foundation to the system.   Clients can easily be rewritten or skinned differently.  Databases on the other hand carry across with them implications such as migrations, history and data volume which in all major modification scenarios often lead to downtime.  Taking that into account it is always a great surprise to me how the database design portion of the product often gets the shortest development cycle in the process.

If you have built a database that was designed to be a single story building, there is no way you can build a second story on top of it without ripping out the foundation that has already been laid.  To maintain database performance it is critical to understand that continuous unplanned additions done in an unplanned way jeopardise the future of the product.  It does not take a rocket scientist to know that no matter how awesome the house looks; if the foundation is faulty, trouble is only a few short CPU cycles around the corner.

This state of being is why it is even more important that the average DB developer be more prepared to produce better designs in the very restricted development windows that exist.

[Read More...](IntroductionToDatabaseDesign.md)

### More about the Author

[Sean Cremer](SeanCremer.md)

## Disclaimer
This is my personal blog. The views expressed on these pages are mine alone and not those of my employer.

© 2017. All rights reserved.


