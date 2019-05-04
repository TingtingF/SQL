# SQL
Module 3


1./*Using a subquery, find the names of all the tracks for the album "Californication".*/

SELECT Name
  FROM Tracks 
 WHERE AlbumId IN (SELECT AlbumId 
                FROM Albums
               WHERE Title = "Californication")
               
 2./*Find the total number of invoices for each customer along with the customer's full name, city and email*/
 
