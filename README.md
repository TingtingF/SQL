# SQL
### Module 3


1./*Using a subquery, find the names of all the tracks for the album "Californication".*/


SELECT Name  
FROM Tracks  
WHERE AlbumId IN (SELECT AlbumId   
                  FROM Albums
               WHERE Title = "Californication")
               
 2./*Find the total number of invoices for each customer along with the customer's full name, city and email*/
 

SELECT SUM(i.InvoiceID) AS totalnumber, c.FirstName, c.LastName, c.Email  
From Invoices i INNER JOIN Customers c  
ON i.CustomerID =  c.CustomerID   
GROUP BY c.CustomerID 


3./*Retrieve the track name, album, artistID, and trackID for all the albums.*/


SELECT t.Name, t.TrackId, a.Title, a.ArtistId  
From Albums a LEFT JOIN Tracks t  
ON a.AlbumId =  t.AlbumId 


4. /*Retrieve a list with the managers last name, and the last name of the employees who report to him or her*/


SELECT M.LastName AS Manager,  
       E.LastName AS Employee  
       FROM Employees E, Employees M   
       WHERE E.ReportsTo = M.EmployeeID



5./*Find the name and ID of the artists who do not have albums.*/


SELECT Name,  
       a.ArtistId,  
       b.Title  
FROM Artists a  
LEFT JOIN Albums b  
ON a.ArtistId = b.ArtistId  
WHERE b.Title IS NULL


6. /*Use a UNION to create a list of all the employee's and customer's first names and last names ordered by the last name in descending order.*/


SELECT FirstName, LastName   
FROM Employees  
  UNION  
  SELECT FirstName, LastName   
  FROM Customers  
  ORDER BY LastName DESC

### Model 4

1. Pull a list of customer ids with the customer’s full name, and address, along with combining their city and country together.  
  
  SELECT CustomerId,  
         FirstName || " " || LastName AS FullName,  
         Address,  
         UPPER(City || " " || Country) AS CityCountry  
         FROM Customers  
           
2. Create a new employee user id by combining the first 4 letters of the employee’s first name with the first 2 letters of the employee’s last name. Make the new field lower case and pull each individual step to show your work.  
  
  SELECT LOWER(SUBSTR(FirstName, 1, 4)||SUBSTR(LastName, 1, 2)) AS EmployeeNewID,  
         LastName, FirstName  
         FROM Employees  
         
         
 3. Show a list of employees who have worked for the company for 15 or more years using the current date function. Sort by lastname ascending.



