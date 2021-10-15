# Create-Database
Simple Database creation for control of inventory.

/*2. Create THE  database */
CREATE DATABASE CDSPaper1.0;
  

USE CDSPaper1.0;
  
/* Create all tables */
CREATE TABLE Sales
(
Sales_id int not null,
Product_id int not null,
Customer_id int not null,
Product_Name varchar(20),
Product_quantity int,
Total_Sale money,
Day_of_Sale datetime
 );
  



CREATE TABLE customer
( 
 Customer_id int, 
 Customer_Name varchar(20),
 Customer_LastName varchar(20),
 Customer_email varchar(30),
 Customer_city varchar(50),
 Customer_Phone varchar(20)
 );

CREATE TABLE products
( 
 product_id int not null,
Product_Name varchar(40),
Product_SalesPrice money not null,
alternate_name varchar(40),
Product_Category varchar(25),
Product_quantity int,
Product_Dimensions int,
reorder_level int,
Average_Cost money 
);
  
CREATE TABLE suppliers
( 
supplier_id int,
Supplier_Name (40) not null,
Supplier_address varchar(30),
Supplier_Contact_Name varchar(30)
Supplier_Contact_Phone int

);

CREATE TABLE Purchases
( 
 Purchases_id int not null,
Supplier_id int,
Product_id int
Product_Total_Cost money not null,
Product_Name varchar(40),
Quantity int,
Date datetime
);


/* Add PK for all tables */
ALTER TABLE customers
ADD PRIMARY KEY ( customer_id )
;
  
ALTER TABLE Sales
ADD PRIMARY KEY (Sales_id );

ALTER TABLE Product
ADD PRIMARY KEY (Product_id );

ALTER TABLE Purchases
ADD PRIMARY KEY (Purchases_id );
  
ALTER TABLE Supplier
ADD PRIMARY KEY (Supplier_id );


ALTER TABLE Sales
ADD CONSTRAINT FK_Product_id FOREIGN KEY (Product_id)
REFERENCES Product
(Product_id);
  
/* Add FK for all tables */
  
ALTER TABLE Sales
ADD CONSTRAINT FK_Customer_id FOREIGN KEY (Customer_id)
REFERENCES Customers
(Customer_id)
;

ALTER TABLE Purchases
ADD CONSTRAINT FK_Supplier_id FOREIGN KEY (Supplier_id)
REFERENCES Supplier
(Supplier_id);


ALTER TABLE Purchases
ADD CONSTRAINT FK_Product_id FOREIGN KEY (Product_id)
REFERENCES Product
(Product_id);
