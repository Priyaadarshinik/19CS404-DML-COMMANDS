# 19CS404-DML-COMMANDS
 
# AIM: 
 
To Study and Implement DML Commands. 
 
# THEORY: 
 
# 1.INSERT INTO: 
 
This is used to add records into a relation. 
These are three type of INSERT INTO queries which are as 
Inserting a single record  
 
Syntax: 
INSERT INTO < relation/table name> (field_1,field_2……field_n)VALUES (data_1,data_2, 
.......data_n);student(sno,sname,class,address)VALUES (1,’Ravi’,’M.Tech’,’Palakol’); 
 
Inserting all records from another relation Syntax: 
INSERT INTO relation_name_1 SELECT Field_1,field_2,field_n FROM relation_name_2 
WHERE field_x=data; 
 
Inserting multiple records Syntax: 
INSERT INTO relation_name field_1,field_2, field_n) VALUES 
(&data_1,&data_2, &data_n); 
 
 
# 2.UPDATE-SET-WHERE: 
 
This is used to update the content of a record in a relation. 
 
Syntax: 
SQL>UPDATE relation name SET Field_name1=data,field_name2=data, WHERE 
field_name=data; Example: SQL>UPDATE student SET sname = ‘kumar’ WHERE sno=1; 
 
# 3.DELETE-FROM: 
This is used to delete all the records of a relation but it will retain the structure of that relation. 
A)DELETE-FROM: This is used to delete all the records of relation. 
NAME: ANU VARSHINI M B   REG NO: 212223240010
 
Syntax: 
DELETE FROM relation_name; 
 
b)DELETE -FROM-WHERE: This is used to delete a selected record from a relation. 
 
Syntax: 
DELETE FROM relation_name WHERE condition; 
 
# 4.SELECT FROM: 
To display a set of fields for all records of relation 
Syntax: 
SELECT (column1,column2) FROM (Table Name)WHERE condition; 
 
 
# Question 1: 
Write a query to fetch 3 top salaried records from the EmployeePosition table. 
EmpID 
EmpPosition 
DateOfJoining 
Salary 
1 
Manager 
01/05/2024 
500000 
2 
Executive 
02/05/2024 
75000 
 
Answer: 
SELECT EmpID,EmpPosition,DateOfJoining,Salary 
FROM EmployeePosition ORDER BY Salary DESC 
LIMIT 3; 
 
Output: 
![image](https://github.com/user-attachments/assets/650f3860-28c9-4e89-b3da-44fd21d63976)


# Question 2: 
Write a SQL query to Select all patients who were admitted for one day. 
name                  type 
--------------------  ---------- 
patient_id            INT 
first_name            VARCHAR(50) 
last_name             VARCHAR(50) 
date_of_birth         DATE 
admission_date        DATE 
discharge_date        DATE 
doctor_id             INT 
 
Answer: 
SELECT patient_id,first_name,admission_date,discharge_date FROM Patients 
WHERE admission_date==discharge_date; 
 
Output: 
![image](https://github.com/user-attachments/assets/ebbeb8db-e75c-490f-a77a-1266c4b9f998)

 
# Question 3: 
Write a SQL query to classify value2 in the Calculations table as 'Small', 'Medium', or 'Large' 
based on whether it is less than 10, between 10 and 50, or greater than 50, respectively. 
 
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ---------- 
0           id          INTEGER     0                       1 
1           value1      REAL        0                       0 
2           value2      REAL        0                       0 
3           base        INTEGER     0                       0 
4           exponent    INTEGER     0                       0 
5           number      REAL        0                       0 
6           decimal     REAL        0                       0 
 
Answer: 
SELECT id,value2,  
CASE WHEN value2<10 
THEN 'Small' 
WHEN value2 BETWEEN 10 AND 50 THEN 'Medium'
ELSE 'Large' 
END AS size_category 
FROM Calculations; 
 
Output: 
![image](https://github.com/user-attachments/assets/e2e740d9-3bf1-456b-ada7-b041220517ac)

 
# Question 4: 
Write a SQL query to find all those customers who does not have any grade. Return customer_id, 
cust_name, city, grade, salesman_id. 
Sample table: customer 

customer_id |   cust_name    |    city    | grade | salesman_id  
-------------+----------------+------------+-------+------------- 
3002         | Nick Rimando   | New York   |   100 |        5001 
3007         | Brad Davis     | New York   |   200 |        5001 
3005         | Graham Zusi    | California |   200 |        5002 
 
Answer: 
SELECT customer_id, cust_name, city, grade, salesman_id 
FROM customer WHERE grade IS NULL; 

 
Output: 
![image](https://github.com/user-attachments/assets/763100c2-9976-4b9b-80c0-b208f2d8bac4)

 
 
# Question 5: 
Write a SQL query to find customers who are either from the city 'New York' or who do not have 
a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id. 
Sample table: customer 

 customer_id |   cust_name    |    city    | grade | salesman_id  
 -------------+----------------+------------+-------+------------- 
3002         | Nick Rimando   | New York   |   100 |        5001 
3007         | Brad Davis     | New York   |   200 |        5001 
3005         | Graham Zusi    | California |   200 |        5003 
 
Answer: 
SELECT customer_id, cust_name, city, grade, salesman_id 
FROM customer 
WHERE city = 'New York' OR grade <=100; 

Output: 
![image](https://github.com/user-attachments/assets/49ce34a8-d8d3-4915-b020-db3f03c46113)

 
 
# Question 6: 
Write a SQL query to identify products where the discount amount is greater than $50. Return 
product_id, original_price, discount_percentage, and discount_amount. 
Sample table: products 
product_id | original_price | discount_percentage  ------------+----------------+---------------------  
101 | 100.00 | 0.60  
102 | 150.00 | 0.40  
103 | 200.00 | 0.10 
 
Answer: 
SELECT product_id, original_price,discount_percentage,original_price * discount_percentage 
AS discount_amount FROM products 
WHERE original_price * discount_percentage > 50; 
 
 
Output: 
![image](https://github.com/user-attachments/assets/8ebfa265-59d4-417c-81cf-51acebc98e14)

 
 
# Question 7: 
Write a SQL query to calculate the original price using the discount percentage and the given 
discounted price. Return product_id, discounted_price, discount_percentage, and original_price. 
Sample table: Products 
product_id | discounted_price | discount_percentage 
 ------------+------------------+--------------------- 
 101 | 45.00 | 0.10  
102 | 63.75 | 0.15  
103 | 80.00 | 0.20 
 
Answer: 
SELECT product_id,discounted_price,discount_percentage, discounted_price/(1
discount_percentage) AS original_price FROM Products; 
 
Output: 
![image](https://github.com/user-attachments/assets/7514464f-58a4-4cc9-9bd1-4e0c23fa2889)


# Question 8: 
Write a SQL query to find all employees along with the day of the week on which they were 
hired from the emp table 
emp table 
cid         name        type         
----------  ----------  ----------  
0           empno       INT          
1           ename       VARCHAR(100) 
2           job         VARCHAR(50) 
3           mgr         INT         
4           hiredate    DATE         
5           sal         DECIMAL(10,2)   
6           comm        DECIMAL(10,2)   
7           deptno      INT     
 
Answer: 
SELECT ename,hiredate, 
CASE strftime('%w',hiredate) 
WHEN '0' THEN 'Sunday' 
WHEN '1' THEN 'Monday' 
WHEN '2' THEN 'Tuesday' 
WHEN '3' THEN 'Wednesday' 
WHEN '4' THEN 'Thursday' 
WHEN '5' THEN 'Friday' 
WHEN '6' THEN 'Saturday' 
END AS day_of_week 
FROM emp; 
 
Output: 
![image](https://github.com/user-attachments/assets/b89946dc-6b69-4c2c-acff-8f3d0d15234e)

 
# Question 9: 
Write a SQL query to find all employees who were hired on a weekend (Saturday or Sunday) 
from the emp table 
emp table 
cid         name        type         
----------  ----------  ----------  
0           empno       INT          
1           ename       VARCHAR(100) 
2           job         VARCHAR(50) 
3           mgr         INT         
4           hiredate    DATE         
5           sal         DECIMAL(10,2)   
6           comm        DECIMAL(10,2)   
7           deptno      INT          
 
Answer: 
SELECT ename,hiredate, 
CASE strftime('%w',hiredate) 
WHEN '0' THEN '0' 
WHEN '6' THEN '6' 
END AS day_of_week 
FROM emp 
WHERE strftime('%w',hiredate) IN ('0','6'); 
 
Output: 
![image](https://github.com/user-attachments/assets/445d18c2-47a0-42aa-b998-aba90c53c798)
 
 
# Question 10: 
Write a SQL query to Concatenate the first three characters of the employee's name with the last 
three characters of their job title. 
Table name: emp 

name        type 
----------  ---------- 
empno       INT 
ename       VARCHAR(100) 
job         VARCHAR(50) 
mgr         INT 
hiredate    DATE 
sal         DECIMAL(10,2) 
comm        DECIMAL(10,2) 
deptno      INT 
 
Answer: 
SELECT ename,job,substr(ename,1,3) || substr(job,-3) 
AS ConcatenatedString FROM emp; 

Output: 
![image](https://github.com/user-attachments/assets/158d19f7-d7fa-4d1d-b666-b332822375a7)

# Result 
Thus , the SQL queries to implement DML commands have been executed successfully. 
 
 
 
# Result 
Thus , the SQL queries to implement DML commands have been executed successfully.
