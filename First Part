```sql
USE assignment_4; 
-- 1st Question
SELECT C.company_name, AVG(I.price) AS 'Average Price' FROM items I
JOIN company C ON I.company_id = C.company_id
GROUP BY C.company_name;

-- 2nd Question
SELECT C.company_name, AVG(I.price) FROM items I
JOIN company C ON I.company_id = C.company_id
GROUP BY C.company_name
HAVING AVG(I.price) > (SELECT AVG(price) FROM items);

-- 3rd Question
SELECT * FROM items
WHERE price > (SELECT AVG(price) FROM items);

-- 4th Question
SELECT * FROM employees e
JOIN departments d ON d.dept_code = e.emp_dept
WHERE d.dept_budget > (SELECT AVG(dept_budget) FROM departments);

-- 5th Question
SELECT d.dept_code, d.dept_name FROM departments d
JOIN employees e ON d.dept_code = e.emp_dept
GROUP BY d.dept_code, d.dept_name
HAVING COUNT(e.emp_id) > (SELECT AVG(emp_count) FROM (SELECT COUNT(emp_id) AS emp_count FROM employees GROUP BY emp_dept) AS dept_count);

-- 6th Question
SELECT * FROM items AS main
WHERE main.price < (
	SELECT AVG(sub.price) 
	FROM items AS sub
	WHERE sub.company_id = main.company_id
);

-- 7th Question
SELECT d.dept_code, d.dept_name, COUNT(e.emp_id) AS Number_of_Employees FROM departments d
JOIN employees e ON d.dept_code = e.emp_dept
GROUP BY d.dept_code, d.dept_name
HAVING COUNT(e.emp_id) = 1;

-- 8th Question
SELECT c.company_name, AVG(i.price) AS Average_Price FROM company c
JOIN items i ON c.company_id = i.company_id
GROUP BY c.company_name
HAVING AVG(i.price) = (SELECT AVG(price) FROM items GROUP BY company_id ORDER BY AVG(price) LIMIT 1);

-- 9th Question
SELECT emp_id, emp_fname, emp_lname, dept_code FROM employees
JOIN departments ON emp_dept = dept_code
WHERE dept_budget < (SELECT AVG(dept_budget) FROM departments);
```
