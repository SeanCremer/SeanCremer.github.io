# Dynamic Mangement Objects (AKA DMVs)

## Table of contents
1. [Introduction](#introduction)
2. [Some Fundamental Truths](#fundamentalTruths)
    1. [-What are some of the Gotchas](#gotachs)
3. [Some Simple Real World Realities](#realities)

<a name="introduction"></a>

## Introduction

In my experience I have never met a real coder who did not want to know more about what was actually going on under the hood of tools and prodcuts that they work with. In the world of Microsoft SQL server getting more metadata has always been something that I have had a great appreciation for.

IN SQL 2005 Dynamic Management Objets (DMOs) were added.  This exposed a whole new world of possibilities. As the versions of MSSQL rolled out so did more DMOs. When working with developers I am often astonished by the notion that they believe that DMOs are there to add value to a DBAs life.  This confuses me immensely as a database developer should be paying attention to a whole bunch more than just indenting their SELECT statements when delivering complex solutions into complex environments.  DMOs provide information that can often change your approach to what you would do in certain situation before you productionise code.  Allowing for better knowledge of the working interplay of an existing system before you introduce something new to it.  Finding out what is happenign under the hood can change direction, thought and strategy with a few simple  SELECT statemetns from some awesome meta data providers, namely DMOs

This post will have quite a few parts continally added to it over the coming weeks to ensure exposure to all the wonders that DMOs provide.  If right now you have no idea what I am talking about with DMOs you probably one of the people that erroneously reference them as DMVs.  I will expalin the differences and eveolution of meta data as whole shortly.


 