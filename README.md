# 25-SQL-QUERIES-WITH-SKYHUB-NIGERIA
![SQL Query](https://github.com/user-attachments/assets/692b413e-37bc-474d-bb6c-108e25a3efdc)

## Table Of Content
- [Project Overview](#project-overview)
- [Beginners Level](#beginners-level)
- [Intermediate Level](#intermediate-level)
- [Advanced Level](#advanced-level)

### Project Overview
SQL (Structured Query Language) Is a "Programming"/Query Language designed for managing and manipulating data stored in Relational Database Management Systems (RDBMs)

This "25 SQL QUERIES WITH SKYHUB NIGERIA" project is focused on carrying out some frequently used and important SQL tasks as a Data Analyst from Beginners Level to Intermediate Level


### Beginners Level

**1. SQL SELECT** 

*-- Write a query to display the first names of all employees from the `employee_demographics` table.*

	SELECT first_name FROM employee_demographics;


**2. SQL LIMIT**

*-- Write a query to display the first three employees from the `employee_salary` table.*

	SELECT * FROM employee_salary
	
	LIMIT 3;


**3. SQL WHERE**

*-- Write a query to find all employees whose age is greater than 40.*

	SELECT * FROM employee_demographics 
	
	WHERE age > 40;


**4. SQL Comparison Operators**

*-- Write a query to find employees with a salary greater than 50,000.*

	SELECT * FROM employee_salary
	
	WHERE salary > 50000;


**5. SQL Logical Operators (AND, OR, NOT)**

*-- Write a query to find employees who are female and older than 30.*

	SELECT * FROM employee_demographics
	
	WHERE gender = "female" AND age > 30;

*-- Write a query to find employees who are male or whose salary is less than 30,000.*

	SELECT gender, salary
	
	FROM employee_demographics
	
	LEFT JOIN employee_salary
	
	ON employee_demographics.employee_id = employee_salary.employee_id
	
	WHERE gender = "male" OR salary < 30000;

*-- Write a query to find employees who are not office managers.*

	SELECT * FROM employee_salary 
	
	WHERE occupation != "office manager";


**6. SQL LIKE**  

*-- Write a query to find all employees whose first name starts with the letter 'A'.*

	SELECT * FROM employee_demographics 
	
	WHERE first_name LIKE 'A%';


**7. SQL IN**

*-- Write a query to find employees who work in departments with IDs 1, 3, and 4.*

	SELECT * FROM employee_salary
	
	WHERE dept_id IN (1, 3, 4);


**8. SQL BETWEEN**

*-- Write a query to find employees whose salary is between 40,000 and 70,000.*
	
	SELECT * FROM employee_salary 
	
	WHERE salary BETWEEN 40000 AND 70000;


**9. SQL IS NULL**

*-- Write a query to find all employees who do not belong to any department.*

	SELECT * FROM employee_salary
	
	WHERE dept_id IS NULL;


**10. SQL ORDER BY**

*-- Write a query to display the employees ordered by their salary in ascending order.*

	SELECT * FROM employee_salary
	
	ORDER BY salary ASC;


**11. SQL COUNT** 

*-- Write a query to count how many employees are in the `employee_demographics` table.*

	SELECT COUNT(*)  AS "TOTAL NUMBER OF EMPLOYEES" FROM employee_demographics;


**12. SQL SUM**

*-- Write a query to find the total salary paid to employees in department 1.*

	SELECT SUM(salary) AS "TOTAL SALARY IN EMPLOYEE 1" FROM employee_salary
	
	WHERE dept_id = 1;


**13. SQL MIN/MAX**

*-- Write a query to find the highest salary in the `employee_salary` table.*

	SELECT MAX(salary) AS "MAXIMUM SALARY" FROM employee_salary;

*-- Write a query to find the lowest age in the `employee_demographics` table.*

	SELECT MIN(age) AS "MINIMUM AGE" FROM employee_demographics;


**14. SQL AVG**

*-- Write a query to calculate the average salary of employees.*

	SELECT AVG(salary) AS "AVERAGE SALARY" FROM employee_salary;


**15. SQL GROUP BY**

*-- Write a query to group employees by gender and count how many employees are male and female.*

	SELECT gender, COUNT(gender) AS "GENDER GROUP" FROM employee_demographics
	
	GROUP BY gender;


**16. SQL HAVING**

*-- Write a query to find the departments where the total salary of employees exceeds 100,000.*

	SELECT dept_id, SUM(salary) AS "TOTAL SALARY" FROM employee_salary
	
	GROUP BY dept_id
	
	HAVING SUM(salary) > 100000;


**17. SQL CASE**

*-- Write a query to classify employees as 'Senior' if their age is 40 or above, and 'Junior' if their age is below 40.*

	SELECT *, 
	
	IF (age >= 40, "Senior", "Junior") AS "CLASSIFICATION" FROM employee_demographics;
	
	-- ALTERNATIVELY
	
	SELECT *, 
	
	CASE 
	
	 	WHEN age >= 40 THEN "Senior"
	
	    ELSE "Junior"
	
	END
	
	AS "CLASSIFICATION" FROM employee_demographics;


**18. SQL DISTINCT**

*-- Write a query to display distinct occupations from the `employee_salary` table.*

	SELECT DISTINCT occupation FROM employee_salary;



### Intermediate Level 


**19. SQL Joins** 

*-- Write a query to display the first name, last name, and department name of employees by joining `employee_salary` and `parks_departments`.*

	SELECT first_name, last_name, department_name
	
	FROM employee_demographics
	
	JOIN parks_departments
	
	ON employee_demographics.employee_id = parks_departments.department_id;


**20. SQL INNER JOIN**  

*-- Write a query to display employees who are in departments (non-NULL department IDs) and their department names.*

	SELECT employee_id, first_name, last_name, age, gender, birth_date, department_name
	
	FROM employee_demographics
	
	INNER JOIN parks_departments
	
	ON employee_demographics.employee_id = parks_departments.department_id;


**21. SQL Outer Joins (LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN)**

*-- Write a query to display all employees and their department names, showing NULL where the employee does not belong to a department (LEFT JOIN).*

	SELECT employee_id, first_name, last_name, age, gender, birth_date, department_name
	
	FROM employee_demographics
	
	LEFT JOIN parks_departments
	
	ON employee_demographics.employee_id = parks_departments.department_id;
    
*--Write a query to display all departments and their employees, showing NULL where no employee is assigned to a department (RIGHT JOIN).*

	SELECT department_id, department_name, employee_id, first_name, last_name, age, gender, birth_date
	
	FROM parks_departments
	
	RIGHT JOIN employee_demographics
	
	ON parks_departments.department_id = employee_demographics.employee_id;


*-- Write a query to display all employees and departments, whether or not they are related (FULL OUTER JOIN).*

	SELECT employee_id, first_name, last_name, age, gender, birth_date, department_id, department_name
	
	FROM employee_demographics
	
	LEFT JOIN parks_departments
	
	ON employee_demographics.employee_id = parks_departments.department_id;

**22. SQL Joins Using WHERE or ON**

*-- Write a query to display employees and their department names using the WHERE clause for the join condition.*

	SELECT first_name, last_name, department_name
	
	FROM employee_demographics
	
	JOIN parks_departments
	
	WHERE employee_demographics.employee_id = parks_departments.department_id;

**23. SQL FULL OUTER JOIN**

*-- Write a query to retrieve all employees and departments with an outer join, ensuring all unmatched rows from both tables are included.*

	SELECT first_name, last_name, department_name
	
	FROM employee_demographics
	
	LEFT JOIN parks_departments
	
	ON employee_demographics.employee_id = parks_departments.department_id;


### Advanced Level

**24. SQL SUB QUERY**

*-- Without Using Sub Query to return the result set of employees using their id from the employee demographics, employee salary table that belongs to department 1*

	SELECT dem.employee_id, dem.first_name, dem.last_name, dem.age, dem.gender, dem.birth_date, sal.dept_id
	
	FROM employee_demographics dem
	
	LEFT JOIN employee_salary sal
	
	ON dem.employee_id = sal.employee_id
	
	WHERE dept_id = 1;

**25. NOW USING SUBQUERIES to achieve 24.**

	SELECT * FROM employee_demographics

	WHERE employee_id IN (
	
	 	SELECT employee_id 
	    FROM employee_salary 
	    WHERE dept_id = 1
	    );
