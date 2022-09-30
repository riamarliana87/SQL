# Ria Marliana's SQL Portfolio

##Welcome to my SQL Portfolio! This code repository contain example of SQL I've written. Feel free to take a look and reach out via email if you have any question : ria.marliana87@gmail.com

-- I have an online shop. I sell 15 types of fashion which are located in 3 warehouses location (Jakarta, Bandung, Semarang). I want to calculate the potential profit in each warehouse if all items are sold.
-- The first thing I did was create a "store" database, then create table named "products". I defined the data type of each field.
-- 1. pid (product id) : INTEGER PRIMARY KEY
-- 2. pname (product name) : TEXT
-- 3. pquantity (quantity of product) : INTEGER 
-- 4. sell_price (sell price per unit) : INTEGER
-- 5. purchase_price (purchase price per unit) : INTEGER
-- 6. wh_loc (warehouse location) : TEXT

CREATE TABLE products (
  pid INTEGER PRIMARY KEY, 
  pname TEXT, 
  pquantity INTEGER, 
  sell_price INTEGER, 
  purchase_price INTEGER,
  wh_loc TEXT);

-- Input the data into each field on product table. 

INSERT INTO products VALUES 
    (1,'Skirt',50,20,15,'Bandung'),
    (2,'Shirt',30,30,15,'Jakarta'),
    (3,'hat',10,10,5,'Jakarta'),
    (4,'Syal',10,5,3,'Jakarta'), 
    (5,'Jacket',20,50,35,'Jakarta'),
    (6,'Pant',35,45,40,'Jakarta'),
    (7,'Short pant',20,25,15,'Jakarta'),
    (8,'Beach pant',40,15,12,'Bandung'),
    (9,'Polo shirt',50,25,20,'Bandung'),
    (10,'T-shirt',60,25,18,'Bandung'),
    (11,'Batik shirt',20,55,50,'Semarang'),
    (12,'underwear',100,10,8,'Semarang'),
    (13,'shoes',200,5,3,'Semarang'),
    (14,'sport pant',30,35,32,'Jakarta'),
    (15,'uniform',20,25,23,'Jakarta');
    
-- Display the database ordered by sell_price
SELECT * FROM products ORDER BY sell_price DESC;

-- Display the sum of product quantity based on warehouse location
SELECT wh_loc, SUM(pquantity) FROM products GROUP BY wh_loc ;

-- Display the product name & its quantity in Jakarta warehouse
SELECT pname,pquantity 
FROM products 
WHERE wh_loc='Jakarta';

-- Display the top 5 of highest profit (sell_price - purchase_price)
SELECT *,(sell_price-purchase_price) AS unit_profit FROM products ORDER BY unit_profit DESC LIMIT 5;
