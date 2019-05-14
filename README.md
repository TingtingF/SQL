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

