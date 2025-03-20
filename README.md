Technologies Used
Programming Language: Python
Database Management System: MySQL
Libraries Used:
mysql-connector (for database connectivity)
tkinter (for GUI, if applicable)
pandas (for data handling)
argparse (for CLI-based operations, if implemented)
Implementation Details
1. Database Structure
A MySQL database is used to store student records, structured as follows:

sql
Copy
Edit
CREATE DATABASE StudentDB;
USE StudentDB;

CREATE TABLE Students (
    RollNumber INT PRIMARY KEY,
    Name VARCHAR(255) NOT NULL,
    Age INT NOT NULL,
    Class VARCHAR(50) NOT NULL,
    Contact VARCHAR(15) NOT NULL
);
2. Python-MySQL Connectivity
The project connects to MySQL using the mysql-connector library and executes CRUD (Create, Read, Update, Delete) operations. Below is an example code snippet for inserting data:

python
Copy
Edit
import mysql.connector

# Establish connection
conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="yourpassword",
    database="StudentDB"
)
cursor = conn.cursor()

# Insert data
query = "INSERT INTO Students (RollNumber, Name, Age, Class, Contact) VALUES (%s, %s, %s, %s, %s)"
values = (101, "John Doe", 20, "CS101", "1234567890")
cursor.execute(query, values)

# Commit changes and close connection
conn.commit()
conn.close()
