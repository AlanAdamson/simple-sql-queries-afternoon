# simple-sql-queries

For today we will be practicing inserting and querying data using SQL.

Here is a website that will let us write queries to interact with some data.  [http://jxs.me/chinook-web/](http://jxs.me/chinook-web/)

On the left are the Tables with their fields.  The right is where we will be writing our queries.  The bottom is where we will see our results.  

Any new tables or records that we add into the database will be removed after you refresh the page.  So if you're wondering where you data went, that may be why.

Use [www.sqlteaching.com](http://www.sqlteaching.com/) or [sqlbolt.com](http://sqlbolt.com/) as resources for the missing keywords you'll need.

## PERSON
1. Create a table called Person that records a person's Name, Age, Height, City, FavoriteColor, and Id.  Id should be an auto-incrementing id/primary key.  
  CREATE TABLE Person
   (
     ID INTEGER PRIMARY KEY AUTOINCREMENT,
     Name TEXT,
     Age INTEGER,
     Height INTEGER,
     City TEXT,
     Favorite_Color
   );

2. Add 5 different people into the Person database.  Remember to not include the Id because it should auto-increment.
  INSERT INTO Person (Name, Age, Height, City, Favorite_Color) VALUES(
    'Alan',
    34,
    6,
    'Provo',
    'Orange'
  );
  INSERT INTO Person (Name, Age, Height, City, Favorite_Color) VALUES(
   'Bob',
   12,
   4,
   'Provo',
   'Red'
 );

 Larry	50	5.8	Orem	Blue

 Moe	80	5.1	LA	Black and White

 INSERT INTO Person (Name, Age, Height, City, Favorite_Color) VALUES(
 'Curly',
 82,
 5.2,
 'New York',
 'White and Black'
);

3. List the people in the Person table by Height from tallest to shortest (descending)
select * from person order by Height desc;

(For this database to create an auto incrementing field set it's type to INTEGER PRIMARY KEY AUTOINCREMENT)

  * List the people in the Person table by Height from shortest to tallest (ascending)
  select * from person order by Height asc;

  * List all the people in the Person table by oldest first
  select * from person order by Age desc;

  * List all the people in the Person table older than age 20.
  select * from person where Age > 20;

  * List all the people in the Person table that are exactly 18.
  select * from person where Age = 18;

  * List all Person that are less than 20 and older than 30.
  select * from person where Age < 20 or Age > 30;

  * List all Person that are not 27 (Use not equals)
  select * from person where Age is not 27;

  * List all Person where their favorite color is not red
  select * from person where Favorite_Color is not 'Red';

  * List all Person where their favorite color is not red or blue
  select * from person where Favorite_Color is not 'Red' and Favorite_Color is not 'Blue';

  * List all Person where their favorite color is orange or green
  select * from person where Favorite_Color is 'Orange' or Favorite_Color is 'Green';

  * List all Person where their favorite color is orange or green blue (use IN)
  select * from person where Favorite_Color in ('Orange', 'Green', 'Blue');

  * List all Person where their favorite color is yellow or purple
  select * from person where Favorite_Color in ('Yellow', 'Purple');

## ORDER
4. Create a table called Orders that records the productName, productPrice, Quantity, and personId  
  CREATE TABLE Orders
     (
       ID INTEGER PRIMARY KEY AUTOINCREMENT,
       productName TEXT,
       productPrice INTEGER,
       Quantity INTEGER
     );

5. Add 5 Orders to Order table
  INSERT INTO Orders (productName, productPrice, Quantity)
  VALUES ('mtn dew', 1.25, 6),
         ('snickers', .85, 2),
         ('lighter', 1, 1),
         ('borrito', 3.50, 6),
         ('chips and salsa', 2.10, 3);

6. Select all the records from the Order table
  SELECT * FROM Orders;

  * Calculate the total number of products Ordered
    SELECT SUM(Quantity) FROM Orders;

  * Calculate the total Order Price
  SELECT SUM(productPrice) FROM Orders;

  * Calculate the total Order Price By personId (If you only made orders for 1 person, go add more for the other people)
  SELECT SUM(productPrice*Quantity) FROM Orders WHERE ID IN (4);

## Artists
7. Add 3 new Artists to the Artist table
INSERT INTO Artist (Name) VALUES
('Circa Survive'),
('Coheed and Cambria'),
('Saosin');

 * Select the top 10 artists in reverse alphabetical order
 SELECT * FROM Artist ORDER BY Name DESC LIMIT 10;

 * Select the top 5 artists in alphabetical order
 SELECT * FROM Artist ORDER BY Name ASC LIMIT 5;

 * Select all artists that start with the word Black
 SELECT * FROM Artist WHERE Name LIKE 'Black%';

 * Select all artists that contain the word Black
 SELECT * FROM Artist WHERE Name LIKE '%Black%';

## Employee
8. Add 2 new Employees to the Employee table
INSERT INTO Employee (EmployeeId, LastName, FirstName, Title, ReportsTo, BirthDate, HireDate, Address, City, State, Country, PostalCode, Phone, Fax, Email)
VALUES (55556, 'Steve', 'Wonder', 'Da Man',	1,	1962-02-18,	2002-08-14,	'11120 Jasper Ave NW',	'Edmonton, AB', 'Canada','T5K','2N1','+1 (780) 428-9482','+1 (780) 428-3457','andrew@chinookcorp.com');

* List all Employee first and last names only that live in Calgary
  SELECT LastName, FirstName FROM Employee WHERE City = 'Calgary';

* Find the first and last name for the youngest employee
SELECT LastName, FirstName, BirthDate FROM Employee ORDER BY BirthDate DESC LIMIT 1;

* Find the first and last name for the oldest employee
SELECT LastName, FirstName, BirthDate FROM Employee ORDER BY BirthDate LIMIT 1;

* Find everyone that reports to Nancy Edwards (Use the ReportsTo column)
SELECT * FROM Employee WHERE ReportsTo = 2;

* Count how many people live in Lethbridge
SELECT * FROM Employee WHERE City = 'Lethbridge';

## Invoice
9. Use the Invoice table for the following

* Count how many orders were made from the USA
* Find the largest order total amount
* Find the smallest order total amount
* Find all orders bigger than $5
* Count how many orders were smaller than $5
* Count how many orders were in CA, TX, or AZ (use IN)
* Get the average total of the orders
* Get the total sum of the orders


## Copyright

© DevMountain LLC, 2016. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.
