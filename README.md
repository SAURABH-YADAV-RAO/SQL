# SQL
SQL QUERY AND SYNTAX FOR PRACTICE

-----DATASET-----
-- USING DATASET AND CREATE TABLE AND INSERT DATA


CREATE TABLE Salesman (
    SalesmanId INT,
    Name VARCHAR(255),
    Commission DECIMAL(10, 2),
    City VARCHAR(255),
    Age INT
);


INSERT INTO Salesman (SalesmanId, Name, Commission, City, Age)
VALUES
    (101, 'Joe', 50, 'California', 17),
    (102, 'Simon', 75, 'Texas', 25),
    (103, 'Jessie', 105, 'Florida', 35),
    (104, 'Danny', 100, 'Texas', 22),
    (105, 'Lia', 65, 'New Jersey', 30);
	
	
	
	
	CREATE TABLE Customer (
    SalesmanId INT,
    CustomerId INT,
    CustomerName VARCHAR(255),
    PurchaseAmount INT,
    );


INSERT INTO Customer (SalesmanId, CustomerId, CustomerName, PurchaseAmount)
VALUES
    (101, 2345, 'Andrew', 550),
    (103, 1575, 'Lucky', 4500),
    (104, 2345, 'Andrew', 4000),
    (107, 3747, 'Remona', 2700),
    (110, 4004, 'Julia', 4545);



CREATE TABLE Orders (OrderId int, CustomerId int, SalesmanId int, Orderdate Date, Amount money)
 

INSERT INTO Orders Values 
(5001,2345,101,'2021-07-01',550),
(5003,1234,105,'2022-02-15',1500)





---Tasks to be Performed:


--1. Insert a new record in your Orders table.

INSERT INTO Orders (OrderId, CustomerId, SalesmanId, Orderdate, Amount)
VALUES (5004, 3747, 103, '2023-08-01', 1200);




--2. Add Primary key constraint for SalesmanId column in Salesman table. Add default
  constraint for City column in Salesman table. Add Foreign key constraint for SalesmanId
  column in Customer table. Add not null constraint in Customer_name column for the
  Customer table.


SP_HELP 'SALESMAN'

ALTER TABLE Salesman
ALTER COLUMN  SalesmanID INT NOT NULL ;




ALTER TABLE Salesman
ADD PRIMARY KEY (SalesmanId);




ALTER TABLE Salesman
ADD CONSTRAINT DF_City DEFAULT 'Unknown' FOR City;



DELETE FROM Customer 
WHERE SalesmanId NOT IN (SELECT SalesmanId FROM Salesman);




ALTER TABLE Customer
ADD CONSTRAINT FK_SalesmanId FOREIGN KEY (SalesmanId) REFERENCES Salesman(SalesmanId);  


ALTER TABLE Customer
ALTER COLUMN CustomerName VARCHAR(255) NOT NULL;






  



----3. Fetch the data where the Customer’s name is ending with ‘N’ also get the purchase
amount value greater than 500.


SELECT *
FROM Customer
WHERE CustomerName LIKE '%N' AND PurchaseAmount > 500;









--4. Using SET operators, retrieve the first result with unique SalesmanId values from two
tables, and the other result containing SalesmanId with duplicates from two tables.


SELECT SalesmanId FROM Salesman
UNION
SELECT SalesmanId FROM Customer;





SELECT SalesmanId FROM Salesman
UNION ALL
SELECT SalesmanId FROM Customer;






--5. Display the below columns which has the matching data.
Orderdate, Salesman Name, Customer Name, Commission, and City which has the
range of Purchase Amount between 500 to 1500.



SELECT Orders.Orderdate, Salesman.Name AS SalesmanName, Customer.CustomerName,
       Salesman.Commission, Salesman.City
FROM Orders
JOIN Customer ON Orders.CustomerId = Customer.CustomerId
JOIN Salesman ON Orders.SalesmanId = Salesman.SalesmanId
WHERE Customer.PurchaseAmount BETWEEN 500 AND 1500;









--6. Using right join fetch all the results from Salesman and Orders table




SELECT *
FROM Salesman
RIGHT JOIN Orders ON Salesman.SalesmanId = Orders.SalesmanId;




*-*-*-*-*-*-*-*-*-**-*-*-*-*-*-*-*-*-*-*-*-***-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*--*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-*-**--*-*-*-*-*-*-*-*-*-*-*-*-*




SELECT * FROM SALESMAN


  SalesmanId	Name	Commission	City	    Age
1 101	        Joe	    50.00	    California	17
2 102	        Simon	75.00	    Texas	    25
3 103	        Jessie	105.00	    Florida	    35
4 104	        Danny	100.00	    Texas	    22
5 105	        Lia	    65.00	    New Jersey	30




SELECT * FROM CUSTOMER 


  SalesmanId	CustomerId	CustomerName	PurchaseAmount
1 101	        2345	    Andrew	        550
2 103	        1575	    Lucky	        4500
3 104	        2345	    Andrew	        4000




SELECT * FROM ORDERS


  OrderId	CustomerId	SalesmanId	Orderdate	Amount
1 5001	    2345	    101	        2021-07-01	550.00
2 5003	    1234	    105	        2022-02-15	1500.00
3 5004	    3747	    103	        2023-08-01	1200.00




