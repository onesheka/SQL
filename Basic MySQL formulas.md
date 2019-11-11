
## MY SQL 

1. SELECT <br>
   - Select * from Table <br>
   - Select <col1,col2> from Table <br>
   - Select Distinct <col1> from Table <br>
   - Select Count(Distinct col1) from Table

2. WHERE <br>
   - SELECT * FROM Table <br>
     WHERE col1 = "blabla"; 
   - Using the operators like =, >, <, >=, <=, <>(!=), BETWEEN, LIKE, IN, AND, OR, NOT <br>
   - BETWEEN: <br>
     SELECT * FROM Table <br>
     WHERE col1 BETWEEN 20 AND 30; <br>
   - NOT BETWEEN: <br>
     SELECT * FROM Table <br>
     WHERE col1 NOT BETWEEN 20 AND 30; <br>
   - LIKE: % - One or more characters , _ represents a single character <br>
     SELECT * FROM table <br>
     WHERE col LIKE 'a%b'; (A string which starts with a and ends with b) <br>
   - WILDCARDS: <br>
     % - Represents one or more charcaters <br>
     _ - Represents a single character <br>
     [a-b] - Represents a range of characters <br>
     [abc] - Represents any character in the bracket <br>
     [^abc] - Represents any character not in the bracket <br>
     [!abc] - Represents any character not in the bracket <br>
   - IN/ NOT IN <br>
     SELECT * FROM table <br>
     WHERE col in[val1,val2,val3]; <br>
   
     
     
    
     
     

3. ORDER BY <br>
   - SELECT * FROM Table <br>
     ORDER BY col1 ASC|DESC; <br>
   - SELECT * FROM Table <br>
     ORDER BY col1 ASC, col2 DESC;

4. INSERT INTO
   - INSERT INTO table(col1,col2,..coln) <br>
     VALUES(val1,val2,...valn); <br>
   - INSERT INTO table <br>
     VALUES(val1,val2.....); <br>

5. IS NULL/ IS NOT NULL
   - SELECT * FROM Table <br>
     WHERE val1 IS NULL <br>
   - SELECT * FROM Table <br>
     WHERE val2 IS NOT NULL <br>
    

6. UPDATE  (Update,set,where)
   - UPDATE Table <br>
     SET col1 = 'blabla', col2 = 'balbla2' <br>
     WHERE col3 = condition; <br>
     

7. DELETE
   - DELETE FROM table <br>
     WHERE col = condition; <br>
   - DELETE FROM table; (To delete all the rows of the table(empty table))

8. TOP, LIMIT, ROWNUM(imp) <br>
   - SELECT TOP 3 FROM table; (Displays first 3 rows of a table) <br>
   - SELECT * FROM table <br>
     LIMIT = 3; <br>
   - SELECT * FROM table <br>
     WHERE ROWUM<=3; <br>
   - SELECT TOP 50 PERCENT * FROM table; <br> (select half of the initial rows of the table) <br>
   (We can also add other clauses like where with these)

9. AGGREAGTE (Min, Max, Count, Average, Sum) <br>
   - SELECT MIN(col1) AS MINPRICE FROM table; <br>
   - SELECT MAX(col2) AS MAXPRICE FROM table; <br>
   - SELECT COUNT(col1) FROM table WHERE condition; <br>
   - SELECT AVG(col) FROM table WHERE condition; <br>
   - SELECT SUM(col) FROM table WHERE condition; <br>

10. ALIASING <br>
    - SELECT CustomerName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country as Address <br>
      FROM Customers; <br>
    - SELECT o.OrderID, o.OrderDate, c.CustomerName <br>
      FROM Customers AS c, Orders AS o <br>
      WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID; <br>
    Aliases can be useful when: <br>

    - There are more than one table involved in a query
    - Functions are used in the query
    - Column names are big or not very readable
    - Two or more columns are combined together

    


11. JOINS <br>
    - INNER JOIN: <br>
      Select table1.col1, table2.col2 <br>
      From table1 <br>
      Inner Join table2 <br>
      On table1.col = table2.col; <br>
    - INNER JOINING 3 tables:<br>
      Select table1.col1, table2.col2, table3.col3<br>
      From ((table1 <br> 
      Inner Join table2 On table1.col = table2.col )<br>
      Inner Join table3 On table1.col = table3.col ); <br>
    - Left Join 
    - Right Join
    - Full Outer Join
    - Self Join: <br>
      SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City <br>
      FROM Customers A, Customers B <br>
      WHERE A.CustomerID <> B.CustomerID <br>
      AND A.City = B.City <br>
      ORDER BY A.City; <br>
    
      
      
      
      

12. UNION / UNION ALL <br>
    - Select col1 from Table1 <br>
      Union     (Only distinct values) <br>
      Select col2 from Table2 <br>
    - SELECT City, Country FROM Customers <br>
      WHERE Country='Germany' <br>
      UNION ALL (ALl the values)<br>
      SELECT City, Country FROM Suppliers <br>
      WHERE Country='Germany' <br>
      ORDER BY City; <br>


13. GROUP BY (Examples) <br>
    - SELECT COUNT(CustomerID), Country <br>
      FROM Customers <br>
      GROUP BY Country; <br>
    - SELECT COUNT(CustomerID), Country <br>
      FROM Customers <br>
      GROUP BY Country <br>
      ORDER BY COUNT(CustomerID) DESC; <br>
    - SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders <br>
      LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID <br>
      GROUP BY ShipperName; <br>
    
         
  

14. HAVING (Just like where clause but used with Aggregate functions) <br>
    - SELECT COUNT(CustomerID), Country <br>
      FROM Customers <br>
      GROUP BY Country <br>
      HAVING COUNT(CustomerID) > 5 <br>
      ORDER BY COUNT(CustomerID) DESC; <br>
    - SELECT COUNT(CustomerID), Country <br>
      FROM Customers <br>
      GROUP BY Country <br>
      HAVING COUNT(CustomerID) > 5 <br>
      ORDER BY COUNT(CustomerID) DESC; <br>
    


15. EXISTS (Examples from w3schools) <br>
    - SELECT SupplierName <br>
      FROM Suppliers <br>
      WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20); <br>
    - SELECT SupplierName <br>
      FROM Suppliers <br>
      WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND Price < 20); <br>



16. ANY / ALL <br>
    - ANY: <br>
      SELECT ProductName <br>
      FROM Products <br>
      WHERE ProductID = ANY (SELECT ProductID FROM OrderDetails WHERE Quantity = 10); <br>
    - ALL: <br>
      SELECT ProductName <br>
      FROM Products <br>
      WHERE ProductID = ALL (SELECT ProductID FROM OrderDetails WHERE Quantity = 10);


17. SELECT INTO <br> (Used to create a new table)
    - Select * Into Newtable <br>
      From OldTable; <br>
    - Select * Into Newtable In 'databse_name' <br>
      From Oldtable; <br>
    - Select table1.col1, table2.col3  (Selecting cols from 2 tables) <br>
      Into Newtable <br>
      From table1 <br>
      Inner Join table2 On table1.col = table2.col; <br>
    - Select * Into Newtable <br>
      From oldtable <br>
      Where 1=0 ; (as this is a condition that will always return false, so empty table will be created) <br>
      

18. INSERT INTO SELECT (Examples from w3schools) <br>
    - INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country) <br>
      SELECT SupplierName, ContactName, Address, City, PostalCode, Country FROM Suppliers; <br>
    - INSERT INTO Customers (CustomerName, City, Country) <br>
      SELECT SupplierName, City, Country FROM Suppliers <br>
      WHERE Country='Germany'; <br>



19. CASE (Examples for W3schools) <br>
    - SELECT OrderID, Quantity, <br>
        CASE <br>
            WHEN Quantity > 30 THEN "The quantity is greater than 30" <br>
            WHEN Quantity = 30 THEN "The quantity is 30" <br>
            ELSE "The quantity is under 30" <br>
        END AS QuantityText <br>
        FROM OrderDetails; <br>
    - SELECT CustomerName, City, Country <br>
        FROM Customers <br>
        ORDER BY <br>
        (CASE <br>
            WHEN City IS NULL THEN Country <br>
            ELSE City <br>
        END); <br>


20. IFNULL FUNCTION (Example from W3schools) <br>
    - SELECT ProductName, UnitPrice * (UnitsInStock + UnitsOnOrder) (Will give error if any UnitsonOrder say has null values<br>
      FROM Products;  <br>
      SOLUTION: <br>
      SELECT ProductName, UnitPrice * (UnitsInStock + IFNULL(UnitsOnOrder, 0)) <br>
      FROM Products; <br>

21. STORED PROCEDURES <br>
    - Creating a Procedure: <br>
      CREATE PROCEDURE SelectAllCustomers <br>
        AS <br>
        SELECT * FROM Customers <br>
        GO; <br>
    - Executing the procedure <br>
       EXEC SelectAllCustomers;
    - Stored Procedures with Parameters: <br>
      CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10) <br>
        AS <br>
        SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode <br>
        GO; <br>
    - EXEC SelectAllCustomers @City = "London", @PostalCode = "WA1 1DP"; <br>
