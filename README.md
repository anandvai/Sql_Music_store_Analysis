# 🎵 Music Store Data Analysis  

## 📌 Project Overview  
This project, **Music Store Data Analysis**, focuses on extracting valuable insights from a music store database. The database includes information about:  

- **Customers** – Purchase patterns and demographics  
- **Employees** – Sales representatives and their performance  
- **Invoices** – Sales transactions and revenue tracking  
- **Tracks & Artists** – Best-selling songs and popular artists  
- **Genres & Playlists** – Music trends and customer preferences  

Using **SQL queries**, we analyze various aspects of the store’s operations.  

---

## 🛠 Tech Stack & Tools  
- **Database:** PostgreSQL / MySQL  
- **Query Language:** SQL  
- **Data Analysis:** Aggregation, filtering, and trend detection  

---

## 📊 SQL Analysis Queries  

### 🔹 Top-Selling Tracks  
```sql
SELECT Track.Name, SUM(Invoice_Line.Quantity) AS TotalSales
FROM Invoice_Line
JOIN Track ON Invoice_Line.Track_Id = Track.Track_Id
GROUP BY Track.Name
ORDER BY TotalSales DESC
LIMIT 10;

 ###  Revenue by Genre
 SELECT Genre.Name, SUM(Invoice_Line.Unit_Price * Invoice_Line.Quantity) AS Revenue
FROM Invoice_Line
JOIN Track ON Invoice_Line.Track_Id = Track.Track_Id
JOIN Genre ON Track.Genre_Id = Genre.Genre_Id
GROUP BY Genre.Name
ORDER BY Revenue DESC;


###🔹 Employee Sales Performance
SELECT 
 Employee.First_Name, 
 Employee.Last_Name, 
 SUM(Invoice.Total) AS TotalSales
FROM Invoice
JOIN Customer ON Invoice.customer_id = Customer.customer_id
JOIN Employee ON CAST(Customer.support_rep_id AS INTEGER) = CAST(Employee.employee_id AS INTEGER)
GROUP BY Employee.First_Name, Employee.Last_Name
ORDER BY TotalSales DESC;


🚀 How to Use
1️⃣ Clone the repository:
git clone <repository_url>
2️⃣ Import the database schema (schema.sql & data.sql) into your PostgreSQL or MySQL database.
3️⃣ Run SQL queries from queries.sql to analyze the dataset.

📬 Contact & GitHub
For any questions or suggestions, feel free to reach out:

👤 Name: Vaibhav Anand
📧 Email: anandvaibhav02@gmail.com
🔗 GitHub: github.com/<your-github-username>

