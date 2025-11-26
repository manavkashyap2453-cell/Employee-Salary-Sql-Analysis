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
4. Find total departments
```sql
select Department 
from employees
group by Department;
```
**There are 5 unique departments**
* Marketing
* HR
* IT
* Finance
* Operations

5. Find which Department has highest count
```sql
select Department,count(EmployeeID)
from employees
group by Department
order by count(EmployeeID) desc limit 1;
```
**Marketing**

6.Find the average and range of experience of employees across the data
```sql
select avg(Experience_Years) as average_experience, 
max(Experience_Years)-min(Experience_Years) as experienc
from employees;
```
* Average experience: '9.9000'
* Range of experience: 19

7. What are the different Education Level and order them according to their count?
```sql
select Education_Level
from employees
group by Education_Level
order by count(EmployeeID) desc;
```
* Master> High School> Phd> Bachelor

8. What is the average age and range of age in our dataset?
```sql
select avg(Age) as average_age, 
min(Age) as minimum_age, 
max(Age) as maximum_age
from employees;
```
* Average age: '39.7600'
* Maximum age: 22
* Minimum age:57
  
9. List down the distinct cities in our dataset
```sql
select distinct(City)
from employees;
```
* Delhi, Bangalore, Hyderabad, Mumbai, Chennai

10.For each department count of employees and avg monthly salary
```sql
select Department,
count(EmployeeID) as employee_count,
avg(Monthly_Salary) as avg_salary
from employees
group by Department
order by avg_salary desc;
```
* 'Marketing' has the highest count of employees with an average salary of '96430.8462'
* 'Operations' has the second highest count of employees with an average salary '84239.9000'

11. For each department find the range and avg of experience
```sql
select Department,
max(Experience_Years)-min(Experience_Years) as experience_range,
avg(Experience_Years) as average_experience
from employees
group by Department
order by average_experience desc;
```
*'Marketing' has range of experience as '11' and has highest average experinece of '12.8462'
* The range of experience in 'IT' is '13' which an average of '10.8000' and it is the second highest



12. For each department find the count of each education level
```sql
select Department, Education_Level,count(EmployeeID)
from employees
group by Department, Education_Level
order by Department;
```


13. Find details of most experienced employee
```sql
select *
from employees
order by Experience_Years desc limit 1;
```

14. Find details of most inexperienced employee
```sql
select *
from employees
order by Experience_Years limit 1;
```

15. Analyze education level of employees in each department in relation to salary
```sql
select Department,Education_Level,avg(Monthly_Salary) as average_salary
from employees
group by Department, Education_Level
order by Department,average_salary desc;
```

16. Find the gender ratio in each department
```sql
select Department, 
round(
sum(case when Gender='Male' then 1 else 0 end)/
sum(case when Gender='Female' then 1 else 0 end)
,2) as male_to_female_ratio
from employees
group by Department;
```

17. Is there a trend between education level and age
```sql
select Education_Level,avg(Age)
from employees
group by Education_Level
order by avg(Age);
```

18. Find average salary of employees in each city
```sql
select City, avg(Monthly_Salary)
from employees
group by City
order by avg(Monthly_Salary) desc;
```

19. Is there an age bias in hiring across different cities or departments?
```sql
select Department, City, avg(Age)
from employees
group by Department, City
order by Department;
```

20.Are certain cities more diverse in terms of gender or education?
```sql
select City,Education_Level,
sum(case when Gender="Male" then 1 else 0 end) as male_employees,
sum(case when Gender="Female" then 1 else 0 end) as female_employees
from employees
group by City,Education_Level
order by City;
```






