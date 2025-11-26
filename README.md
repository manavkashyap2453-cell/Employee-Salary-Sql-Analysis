# Employee Data Analysis (SQL Project)

## Overview
This project focuses on analyzing employee-related data using **SQL queries**.  
The dataset contains information such as employee demographics, experience, education, and salary.  
The goal is to uncover insights into workforce diversity, compensation equity, and career progression, while also answering predictive and strategic questions.

---
![imagealt](ai-generated-8876488_1280.png)

## 📂 Dataset Structure
The dataset includes the following columns:

- **EmployeeID**: Unique identifier for each employee  
- **Name**: Employee name  
- **Department**: Department of employment  
- **Experience_Years**: Total years of work experience  
- **Education_Level**: Highest education qualification  
- **Age**: Employee age  
- **Gender**: Employee gender  
- **City**: Location of employment  
- **Monthly_Salary**: Current monthly salary

## SQL Queries involved

1. Create a database for our data
   ```sql
   create database if not exists analysis;
   use analysis;
   ```
2. Create a table for importing the data
   ```sql
   create table employees(
   EmployeeID INT PRIMARY KEY,
   Name VARCHAR(20),
   Department	VARCHAR(15),
   Experience_Years INT,
   Education_Level	VARCHAR(20),
   Age	INT,
   Gender	VARCHAR(10),
   City VARCHAR(15),
   Monthly_Salary INT
   );
   ```
3. View the entire table
```sql
select * from employees;
```
4. Find total departments\
```sql
select Department 
from employees
group by Department;
```

5. Find which Department has highest count
```sql
select Department,count(EmployeeID)
from employees
group by Departmente
order by count(EmployeeID) desc limit 1;
```

6.Find the average and range of experience of employees across the data
```sql
select avg(Experience_Years) as average_experience, 
max(Experience_Years)-min(Experience_Years) as experienc
from employees;
```

7. What are the different Education Level and order them according to their count?
```sql
select Education_Level
from employees
group by Education_Level
order by count(EmployeeID) desc;
```

8. What is the average age and range of age in our dataset?
```sql
select avg(Age) as average_age, 
min(Age) as minimum_age, 
max(Age) as maximum_age
from employees;
```

9. List down the distinct cities in our dataset
```sql
select distinct(City)
from employees;
```



