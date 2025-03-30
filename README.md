Music Store Data Analysis

Project Overview
This project, Music Store Data Analysis, involves analyzing data from a music store database to extract insights about sales, customers, employees, and tracks. The database schema is designed to store information about customers, employees, invoices, playlists, tracks, artists, and more, enabling comprehensive analysis of the store's operations.

Database Schema
(Include an ER diagram here if available.)

Analysis Queries
Here are some example queries used for analysis:

Top-selling tracks:
SELECT Track.Name, SUM(Invoice_Line.Quantity) AS TotalSales
FROM Invoice_Line
JOIN Track ON Invoice_Line.Track_Id = Track.Track_Id
GROUP BY Track.Name
ORDER BY TotalSales DESC
LIMIT 10;


Revenue by genre:
SELECT Genre.Name, SUM(Invoice_Line.Unit_Price * Invoice_Line.Quantity) AS Revenue
FROM Invoice_Line
JOIN Track ON Invoice_Line.Track_Id = Track.Track_Id
JOIN Genre ON Track.Genre_Id = Genre.Genre_Id
GROUP BY Genre.Name
ORDER BY Revenue DESC;


Employee sales performance:
SELECT 
 Employee.First_Name, 
 Employee.Last_Name, 
 SUM(Invoice.Total) AS TotalSales
FROM Invoice
JOIN Customer ON Invoice.customer_id = Customer.customer_id
JOIN Employee ON CAST(Customer.support_rep_id AS INTEGER) = CAST(Employee.employee_id AS INTEGER)
GROUP BY Employee.First_Name, Employee.Last_Name
ORDER BY TotalSales DESC;


How to Use
Clone the repository:
git clone <repository_url>
Import the schema and data files into your PostgreSQL or MySQL database.
Run the queries from queries.sql to perform the analysis.
Tools Used
Database Management: PostgreSQL

SQL Queries: For data manipulation and analysis

Contact
For any questions or suggestions, feel free to reach out:

Name: Vaibhav Anand

Email: anandvaibhav02@gmail.com