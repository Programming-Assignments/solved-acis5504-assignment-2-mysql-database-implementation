Download Link: https://assignmentchef.com/product/solved-acis5504-assignment-2-mysql-database-implementation
<br>



This assignment involves querying four tables (Customer, Order, Order Line, and Product) in a MySQL database. The table contents are listed below. Instructions on how to operate MySQL and how to create tables manually are described below. The tables should be in your MySQL database prior to executing these queries.

The activities of this assignment are covered in Modules 1 through 8, and implement course objectives #2 thru #5:

<ol start="2">

 <li>Create entity-relationship models for business and other situations</li>

 <li>Convert entity-relationship models into relational models</li>

 <li>Use SQL to create tables, indexes, and views for business and other situations</li>

 <li>Use SQL to insert, update, and delete rows in tables</li>

</ol>

<strong> To complete assignment, you should complete the following activities:</strong>

<ul>

 <li>Read Chapter 7: Introduction to Structured Query Language (SQL)</li>

 <li>Review the slides and recorded lectures for Chapter 7</li>

 <li>Read Chapter 8: Advanced SQL</li>

 <li>Review the slides and recorded lectures for Chapter 8</li>

 <li>Review the MySQL website</li>

 <li>Complete the step-by-step activities listed below under submission requirements.</li>

</ul>

<strong>Assignment Resources</strong>

<ul>

 <li>Recorded lectures for Chapters 7 and 8</li>

 <li>Recorded lecture slides for Chapters 7 and 8</li>

 <li>Youtube or other tutorials for using MySQL</li>

 <li>Link to the <a href="https://canvas.vt.edu/courses/102788/discussion_topics/651390"><strong>Assi</strong></a><a href="https://canvas.vt.edu/courses/102788/discussion_topics/651390"><strong>g</strong></a><a href="https://canvas.vt.edu/courses/102788/discussion_topics/651390"><strong>nment 2 Questions and Answers</strong></a> Discussion</li>

</ul>

<strong><u>Directions</u></strong>: This is assignment is conceptually simple and is intended to get you started on the mechanics of using the popular MySQL DBMS.  The only submission requirement is the quiz.

<strong><u>Submission Requirements </u></strong><u> </u>

<h2>1) Download and install a free version of MySQL (5 points)</h2>

Obtain the latest version of MySQL free from the MySQL website.

<em>Installing MySQL (on Windows)</em>

The latest is provided in a Zip archive, which contains one file called “Setup.exe”. Unzip the archive and run “Setup.exe”. When the setup program begins, it will ask you whether you want a “Typical”, “Complete”, or “Custom” installation. I suggest choosing a “Typical” installation, since that suffices for our course, and will save you from having to answer questions that you may not be prepared to answer.

Next, you’ll be asked to sign up for a MySQL.com account. This is up to you, and it’s not a requirement.

After that, you’ll be told that the setup wizard is finished, and you’ll be offered the chance to “Configure the MySQL Server now”. Make sure this checkbox is checked (it should be by default) and click “Finish”.

You’ll now be taken into a new wizard that will configure your installation of MySQL. What follows is a list of choices that I suggest you make as you work your way through each page of the wizard: a. Select “Standard Configuration” and click “Next”.

<ol>

 <li>Make sure the checkboxes “Install As Windows Service”, “Launch the MySQL Server automatically”,and “Include Bin Directory in Windows PATH” are all checked, and use “MySQL” as the service name.</li>

</ol>

Click “Next”.

<ol>

 <li>Make sure the “Modify Security Settings” checkbox is checked and that the others are not. Choose apassword and enter it into the “New root password” and “Confirm” boxes. Don’t forget this password!</li>

</ol>

Click “Next”.

<ol>

 <li>Click “Execute” to start the configuration process. When it’s done, click “Finish”.</li>

</ol>

Congratulations! MySQL 5.0 is now installed on your computer and ready to use for your assignments (or whatever else).

The “server” will be running in the background whenever your computer is running, so you can connect to it anytime using the mysql command-line program (use only the command line program for this assignment).

It’s possible from time to time that you may need to know what port MySQL Server is running on. By default, it runs on port 3306.

During the installation process, MySQL will ask that you designate a root password to log in to each MySQL session. Please assign a password and remember it as you will need it every time you use MySQL.

<em>Using your MySQL password and creating a simple test database</em>

The command-line parameters tell mysql to connect to the server using the username “root” (which was created for you during the installation process and has full rights to do anything) and to allow you to type the root password (the password for the “root” username) when the program starts. Without the -password option, you simply won’t be able to connect to the server, so be sure to include this option. When asked, type the root password you specified during installation, and you should see something like this:

Welcome to the MySQL monitor. Commands end with ; or g.

Your MySQL connection id is 5 to server version: 5.0.18-nt

Type ‘help;’ or ‘h’ for help. Type ‘c’ to clear the buffer.

mysql&gt;

The prompt mysql&gt; is where you type SQL commands. To verify that things are working correctly, go through the following steps to create a simple database and query it. In the text below, boldfaced text indicates something that you should type, while normal-weight text indicates something that the mysql program will print in response.

mysql&gt; CREATE DATABASE test184; Query OK, 1 row affected (0.00 sec)

mysql&gt; USE test184; Database changed mysql&gt; CREATE TABLE customer( -&gt; customer_id INTEGER,

-&gt; customer_name CHAR(30),

-&gt; customer_city CHAR(20),

-&gt; PRIMARY KEY(customer_id)); Query OK, 0 rows affected (0.16 sec)

mysql&gt; INSERT INTO customer VALUES (1, ‘Ann’, ‘Irvine’); Query OK, 1 row affected (0.08 sec)

mysql&gt; INSERT INTO customer VALUES (2, ‘Joe’, ‘Mission Viejo’);

Query OK, 1 row affected (0.09 sec)

mysql&gt; SELECT * FROM customer

-&gt; WHERE customer_city = ‘Irvine’;

+————-+—————+—————


| customer_id | customer_name | customer_city |

+————-+—————+—————


| 1 | Ann | Irvine |

+————-+—————+—————


1 row in set (0.00 sec)

mysql&gt; DROP DATABASE test184; Query OK, 1 row affected (0.09 sec)

mysql&gt; q

Bye

Creating assignment

<h2>2) Create and populate the following tables in your MySQL database (5 points)</h2>

Ok, now you are ready to create the Pine Valley Furniture database that you will use for assignment #2. Based on the example above, use the SQL commands below to create the database and tables for this assignment.

CREATE DATABASE PineValleyFurniture;

USE PineValleyFurniture;

The Pine Valley Furniture Company has the following entities. As manager of a retail location, you need to query your database to determine certain trends and relationships in customer, product, and order activity.

<em>Use these CREATE TABLE statements for your database.</em>

CREATE TABLE Customer_t (

Customer_ID INTEGER,

Customer_Name CHAR (30),

Customer_Address VARCHAR (30),

City CHAR (30),

State CHAR (30),

Postal_Code VARCHAR (5),

PRIMARY KEY (Customer_ID));

CREATE TABLE Product_t (

Product_ID INTEGER,

Product_Description CHAR (30),

Product_Finish CHAR (30),

Standard_Price INTEGER,

Product_Line_ID INTEGER,

PRIMARY KEY (Product_ID));

CREATE TABLE Order_t (

Order_ID INTEGER,

Order_Date DATE,

Customer_ID INTEGER,

PRIMARY KEY (Order_ID));

CREATE TABLE Order_Line_t (

Order_ID INTEGER,

Product_ID INTEGER,

Quantity_Ordered INTEGER);

<em>Use these INSERT statements to populate your tables.</em>




INSERT INTO Customer_t VALUES (1, “Contemporary Casuals”, “1355 S. Hines Blvd.”, “Gainesville”, “FL”, 32601);

INSERT INTO Customer_t VALUES (2, “Value Furniture”, “15145 S.W. 17th St.”, “Plano”, “TX”, 75094);

INSERT INTO Customer_t VALUES (3, “Home Furnishings”, “1900 Allard Ave.”, “Albany”, “NY”, 12209);

INSERT INTO Customer_t VALUES (4, “Eastern Furniture”, “1925 Beltline Rd.”, “Carteret”, “NJ”, 07008);

INSERT INTO Customer_t VALUES (5, “Impressions”, “5595 Westcott Ct.”, “Sacramento”, “CA”, 94206);

INSERT INTO Customer_t VALUES (6, “Furniture Gallery”, “325 Flatiron Dr.”, “Boulder”, “CO”, 80514);

INSERT INTO Customer_t VALUES (7, “Period Furniture”, “394 Rainbow Dr.”, “Seattle”, “WA”, 97954);

INSERT INTO Customer_t VALUES (8, “California Classics”, “816 Peach Rd.”, “Santa Clara”, “CA”, 69615);

INSERT INTO Customer_t VALUES (9, “M and H Casual Furniture”, “3709 First Street”, “Clearwater”, “FL”, 34620);

INSERT INTO Customer_t VALUES (10, “Seminole Interiors”, “2400 Rocky Point Dr.”, “Seminole”, “FL”, 34646);

INSERT INTO Customer_t VALUES (11, “American Euro Lifestyles”, “2424 Missouri Ave N.”, “Prospect

Park”, “NJ”, 07508);

INSERT INTO Customer_t VALUES (12, “Battle Creek Furniture”, “345 Capitol Ave SW”, “Battle Creek”, “MI”, 49015);

INSERT INTO Customer_t VALUES (13, “Heritage Furnishings”, “66789 College Ave”, “Carlisle”, “PA”, 17013);

INSERT INTO Customer_t VALUES (14, “Kaneohe Homes”, “112 Kiowai St.”, “Kaneohe”, “HI”, 96744);

INSERT INTO Customer_t VALUES (15, “Mountain Scenes”, “4132 Main Street”, “Ogden”, “UT”, 84403); *****

INSERT INTO Product_t VALUES (1, “End Table”, “Cherry”, 175, 1);

INSERT INTO Product_t VALUES (2, “Coffee Table”, “Natural Ash”, 200, 2);

INSERT INTO Product_t VALUES (3, “Computer Desk”, “Natural Ash”, 375, 2);

INSERT INTO Product_t VALUES (4, “Entertainment Center”, “Natural Maple”, 650, 3);

INSERT INTO Product_t VALUES (5, “Writers Desk”, “Cherry”, 325, 1);

INSERT INTO Product_t VALUES (6, “8 Drawer Desk”, “White Ash”, 750, 2);

INSERT INTO Product_t VALUES (7, “Dining Table”, “Natural Ash”, 800, 2);

INSERT INTO Product_t VALUES (8, “Computer Desk”, “Walnut”, 250, 3);




*****

INSERT INTO Order_Line_t VALUES (1001, 1, 2);

INSERT INTO Order_Line_t VALUES (1001, 2, 2);

INSERT INTO Order_Line_t VALUES (1001, 4, 1);

INSERT INTO Order_Line_t VALUES (1002, 3, 5);

INSERT INTO Order_Line_t VALUES (1003, 3, 3);

INSERT INTO Order_Line_t VALUES (1004, 6, 2);

INSERT INTO Order_Line_t VALUES (1004, 8, 2);

INSERT INTO Order_Line_t VALUES (1005, 4, 4);

INSERT INTO Order_Line_t VALUES (1006, 4, 1);

INSERT INTO Order_Line_t VALUES (1006, 5, 2);

INSERT INTO Order_Line_t VALUES (1006, 7, 2);

INSERT INTO Order_Line_t VALUES (1007, 1, 3);

INSERT INTO Order_Line_t VALUES (1007, 2, 2);

INSERT INTO Order_Line_t VALUES (1008, 3, 3);

INSERT INTO Order_Line_t VALUES (1008, 8, 3);

INSERT INTO Order_Line_t VALUES (1009, 4, 2);

INSERT INTO Order_Line_t VALUES (1009, 7, 3);

INSERT INTO Order_Line_t VALUES (1010, 8, 10);




*****

INSERT INTO Order_t VALUES (1001, “2004-10-21”, 1);

INSERT INTO Order_t VALUES (1002, “2004-10-21”, 8);

INSERT INTO Order_t VALUES (1003, “2004-10-22”, 15);

INSERT INTO Order_t VALUES (1004, “2004-10-22”, 5);

INSERT INTO Order_t VALUES (1005, “2004-10-24”, 3);

INSERT INTO Order_t VALUES (1006, “2004-10-24”, 2);

INSERT INTO Order_t VALUES (1007, “2004-10-27”, 11);

INSERT INTO Order_t VALUES (1008, “2004-10-30”, 12);

INSERT INTO Order_t VALUES (1009, “2004-11-05”, 4);

INSERT INTO Order_t VALUES (1010, “2004-11-05”, 1);

<strong><em>Once all the tables are created and populated you are ready to start querying the Pine Valley Furniture database to answer the questions for this quiz. </em></strong>

<ul>

 <li><strong>(Requirement 3.1) List the standard price, product description, and product ID for all productsin the product table (1 point)</strong></li>

 <li><strong>(Requirement 3.2) Which products have a standard price of less than $275? (Hint: Display the product description and the standard price) </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.3) What is the average standard price for all products in the products table? </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.4) How many different types (count) of products were ordered on order number 1004? </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.5) Display the order ID and the order date for orders have been placed since</strong></li>

</ul>

<strong>10/24/2004? (Hint: This is exclusive, meaning everything after 10/24) </strong><strong>(1 point)</strong>

<ul>

 <li><strong>(Requirement 3.6) What furniture does Pine Valley carry that isn’t made of Cherry? Output should show description and finish. </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.7) List all customers who live in warmer states (Define warmer states to be Florida, Texas, California, and Hawaii). List the customers alphabetically first by state, then by customer name. Add the attribute City (from Customer_t) as an additional column for more</strong></li>

</ul>

<h2>detail. (1 point)</h2>

<ul>

 <li><strong>(Requirement 3.8) Find only states with more than one customer. List the state in which they reside and the number of customers in that state. </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.9) List the product finish and the average standard price for that finish for every product finish whose average standard price is less than $750. (Hint: Display product finish and price) (Hint 2: Cherry has an average price of $250) </strong><strong>(1 point)</strong></li>

 <li><strong>(Requirement 3.10) List the Product ID, Description, Finish, and Standard price from the</strong></li>

</ul>

<strong>Products table for those products that have a price less than the average price for ALL products. (Hint: If the average price for all products is $10, then select all products which have price less than $10.) </strong><strong>(1 point)</strong>

<ul>

 <li><strong>(Requirement 3.11) Create a VIEW named Product_V that consists of product description, finish, and standard price. Use the Product view to list the product description, finish, and standard price for all desks and/or tables that cost more than $300. </strong><strong>(1 point)</strong></li>

</ul>

Hint #1 — Need to see SQL code for both the creation of the VIEW and the querying of the newly created VIEW with output)

Hint #2 – Create the VIEW that contains the data of interest, then query the entire VIEW like a table Hint #3 – Your output will not include the entertainment center (it’s neither a desk nor a table), but your query will not necessarily exclude it.

<ul>

 <li><strong>(Requirement 3.12) Create an INDEX named Furniture on the Product_Finish column of the</strong></li>

</ul>

<strong>Product_t table. Use this index to retrieve records from the product_t table. </strong><strong>(2 points)</strong>

Submit DDL for the creation of the INDEX and the SQL query on the products table that uses the index, i.e., includes the Product_Finish column in the WHERE clause.

NOTE: Given the small size of this database, you will see no improvement in performance. But please keep in mind that indexing a larger database with millions of records, it would make a sizable difference.

NOTE: In terms of decimal points, I don’t have a preference for how they are displayed.

<strong>Assessment</strong>

The activities in this assignment are expected to be simple for you to complete. So, for each activity little partial credit is possible. However, you can receive partial credit for the entire assignment by not completing some of the activities.

<strong>Connecting Assignments</strong>

This assignment gives you some hands-on experience with a popular database tool.


