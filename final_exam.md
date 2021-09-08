# FINAL EXAM

## Final Exam: Question 1

Problem:

Scenario

Consider the following information about the operations on a system:

Write Operations

https://university-courses.s3.amazonaws.com/M320/m320-final-question1-writes-v2.png
ID - A unique value to identify each operation.
Description - A summary of the action occuring in the application that triggers this operation.
Type - Additional information about whether this operation is an insert operation or an update operation.
Durability - The number of nodes that must write the data to the database for the operation to be considered complete.
Data Life - The amount of time this record will be stored in the database.
Data Size - The number of bytes being written to the database.
Storage Size - The amount of additional storage needed per day to store all new write data for this operation.
Average Frequency - The average number of times this operation occurs per second.
Peak Frequency - The average number of times this operation occurs per second at peak hour frequency.
Read operations

https://university-courses.s3.amazonaws.com/M320/m320-final-question1-reads.png
ID - A unique value to identify each operation.
Description - A summary of the action occuring in the application that triggers this operation.
Type - Additional information about whether this operation is a real-time operation or an analytics operation.
Max Latency - The maximum acceptable amount of time for the application to wait to receive data from the database.
Execution Time - The average amount of time the operation takes to complete. This is only filled in if the amount of time is longer than 1 second.
Single Doc Size - The average size of the document being retrieved.
Average Frequency - The average number of times this operation occurs per second.
Peak Frequency - The average number of times this operation occurs per second at peak hour frequency.
Which of the following operations is the one that should be considered most prominently when designing our schema?

Attempts Remaining:Correct Answer

Choose the best answer:

- [ ] W4 - application records time and user info when an item is viewed.
- [ ] W6 - user adds item to cart.
- [ ] R1 - user logs into the application.
- [X] R2 - user views a specific item.
- [ ] R4 - user views their cart.

## Final Exam: Question 2

Problem:

Scenario

We built a very successful navigation application for cell phones. The application has been installed on many devices throughout the world.

Over a long period of time, the application is active on an average of 10 million cell phones, with a maximum peak of 50 million devices at the busiest time of the year. This average value includes all of the peaks.

Each device, when active, sends 100 bytes of data every minute, which the server writes as one operation.

We want to keep the data for one year.

Based on the above numbers, which of the following are true statements regarding the quantification of this workload and the sizing of the database?

To simplify the calculations and conversions in data units, use:

1,000,000,000 bytes is 1 gigabyte
1,000,000,000,000 bytes is 1 terabyte
1,000,000,000,000,000 bytes is 1 petabyte
and round all results to 2 significant digits.

Attempts Remaining:3 Attempts left

Check all answers that apply:

- [ ] The size of the data in the database is 2.6 terabytes.
- [X] The size of the data in the database is 530 terabytes.
- [ ] The size of the data in the database is 2.6 petabytes.
- [ ] The peak write rate is 17,000 writes/second.
- [ ] The peak write rate is 170,000 writes/second.
- [X] The peak write rate is 830,000 writes/second.
- [ ] The average write rate is 17,000 writes/second.
- [ ] The average write rate is 83,000 writes/second.
- [X] The average write rate is 170,000 writes/second.

## Final Exam: Question 3

Problem:

Given the following Collection Entity Diagram.

https://university-courses.s3.amazonaws.com/M320/product_catalog_relationships-1-1_ref_second.png
Which of the following pairs of data have a One-to-One relationship between them?

Attempts Remaining:3 Attempts left

Check all answers that apply:

- [X] stores.address and store_details.manager.name
- [X] stores.name and store_details.description
- [X] stores.name and stores.city
- [ ] stores._id and store_details.services
- [ ] stores.name and store_details.staff.name
- [ ] store_details.manager.employee_id and store_details.staff.employee_id
- [ ] store_details.name and store_details.staff.name

## Final Exam: Question 4

Problem:

We are building a social media site where users can share a lot of details about their whereabouts in their lives.

The site will likely have many European customers. For all these users, the GDPR law in Europe cites that a person has the right to be forgotten, meaning all data related to that person should be erased per request of the user.

Which one of the following implementations would be the preferred way to represent the One-to-Many relationship between restaurants and each user's last-visited restaurant to enable easy removal of a user's activity in accordance with GDPR?

Choose the best answer:

- [ ] Only a users collection in which all restaurant information is embedded.
https://university-courses.s3.amazonaws.com/M320/m320-final-one-to-many-4.png

- [ ] A restaurants collection with references to users documents.
https://university-courses.s3.amazonaws.com/M320/m320-final-one-to-many-3.png

- [ ] Only a restaurants collection in which all user information is embedded.
https://university-courses.s3.amazonaws.com/M320/m320-final-one-to-many-2.png

- [X] A users collection with an extended reference to a restaurants document.
https://university-courses.s3.amazonaws.com/M320/m320-final-one-to-many-1.png

## Final Exam: Question 5

Problem:

Which of the following are recommended ways to model a Many-to-Many relationship between airlines and the cities those airlines fly between?
Attempts Remaining:3 Attempts left

Check all answers that apply:

- [X] Referencing the airlines documents in each of the corresponding cities documents.
https://university-courses.s3.amazonaws.com/M320/m320-final-many-to-many-2.png

- [X] Embedding the airlines that fly to/from a city in each of the corresponding cities document and keeping a separate copy of the airlines documents.
https://university-courses.s3.amazonaws.com/M320/m320-final-many-to-many-1.png

- [ ] Embedding the airlines that fly to/from a city in each of the corresponding cities document, without having a separate collection for the airlines.
https://university-courses.s3.amazonaws.com/M320/m320-final-many-to-many-3.png

## Final Exam: Question 6

Problem:

Consider a system that collects census data on all countries in the world.

Which of the following implementations are recommended ways to model a One-to-Zillions relationship between a person entity and the country entity in which that person was born?

Check all answers that apply:

- [X] Referencing from the Zillions side. In each person document, we reference the corresponding country document.
- [ ] Embedding as an array.In the document for a country, we embed all the people born in that country.
- [ ] Referencing from the One side. In the document for a country, we have an array of references to the documents of the people who are kept in a separate collection.

## Final Exam: Question 7

Problem:
Scenario

Your team just hired a new Data Architect, and her amazing ideas are gaining traction with the company leadership.

You already updated your application to be able to handle the new data organization in your database. Now you have been tasked with implementing her proposed new data organization approach to your database with minimum downtime for the users of the application.

Which pattern solution is best suited for this situation?

Choose the best answer:

- [ ] The Attribute Pattern
- [ ] The Extended Reference Pattern
- [ ] The Subset Pattern
- [ ] The Bucket Pattern
- [X] The Schema Versioning Pattern

## Final Exam: Question 8

Problem:

Scenario

A new decision maker came aboard your online bookstore team. They want to be able to track which genres are most popular daily. To keep this metric up to date without running massive queries for obtaining it, which of the following schema patterns would you choose to implement?

Choose the best answer:

- [ ] The Extended Reference Pattern
- [ ] The Subset Pattern
- [ ] The Polymorphic Pattern
- [ ] The Bucket Pattern
- [X] The Computed Pattern

## Final Exam: Question 9

Problem:

Scenario

You work as a developer at a factory. Your factory wants to track the usage statistics of the automatic lighting that was recently installed throughout its facilities. The lights send an update to the database every 10 seconds, but the management is interested in an hourly report instead. Additionally, we are only looking to store this information for at most 5 years, so an easy way to purge old data would be beneficial to our data modeling approach.

Which pattern solution is best suited for this situation?

Choose the best answer:

- [ ] The Computed Pattern
- [X] The Bucket Pattern
- [ ] The Polymorphic Pattern
- [ ] The Subset Pattern
- [ ] The Extended Reference Pattern

## Final Exam: Question 10

Problem:

Scenario

With the digitization of every area of our lives, the famous NYC bodegas (convenience stores) are trying to keep up. Bodegas don't just know everything that goes on in the neighborhood, they also supply all types of household goods, hardware supplies, and groceries. The New York City Bodega Association is looking to create an app that will help them keep track of their unique, versatile inventory and help customers look up whether items are in stock before visiting the bodega.

Which pattern solution is best suited for this application?

Choose the best answer:

- [ ] The Extended Reference Pattern
- [X] The Polymorphic Pattern
- [ ] The Bucket Pattern
- [ ] The Computed Pattern
- [ ] The Subset Pattern

## Final Exam: Question 11

Problem:

Scenario

You are a developer working on an e-commerce application. Each time your application retrieves an item from the inventory collection, it also needs to retrieve data about the orders in which this item is present. This leads to additional queries on the orders collection.

We know that reducing the total number of queries we perform on the system would solve the main performance issue we are seeing at peak time.

Which pattern solution is best suited for this situation?

Choose the best answer:

- [ ] The Computed Pattern
- [X] The Extended Reference Pattern
- [ ] The Bucket Pattern
- [ ] The Schema Versioning Pattern
- [ ] The Polymorphic Pattern

## Final Exam: Question 12

Problem:

Scenario

As a chemical manufacturer, you tend to keep your factory and your data organized, since dealing with chemicals requires a lot of precision, attention, and safety mechanisms. One of the safety mechanisms in the factory is the documentation about produced chemicals. This documentation is recorded in Material Safety Data Sheets which are large pdf documents containing safety details about a given chemical. These Data Sheets are part of the documents in the inventory collection, where other information such as the price, quantity, and warehouse location of the chemical is stored as well.

Keeping track of production, sales, and purchases requires a lot of data manipulation on an hourly basis. You notice that at especially busy times, your inventory tracking application slows down by a lot.

Which pattern solution is best suited for solving this issue?

Choose the best answer:

- [ ] The Bucket Pattern
- [ ] The Polymorphic Pattern
- [X] The Subset Pattern
- [ ] The Computed Pattern
- [ ] The Extended Reference Pattern
