```sql
-- 1st Question
WITH Average_Item_Price AS (SELECT AVG(price) AS Average_Price FROM items)
SELECT * FROM items
WHERE price > (SELECT Average_Price FROM Average_Item_Price);

-- 2nd Question
WITH number_of_items_per_company_CTE
AS (SELECT company_id, COUNT(item_id) AS number_of_items FROM items GROUP BY company_id)
SELECT c.company_name, i.number_of_items FROM company c
JOIN number_of_items_per_company_CTE i ON c.company_id = i.company_id;

-- 3rd Question
WITH average_price_per_company_CTE
AS (SELECT company_id, AVG(price) AS average_price FROM items GROUP BY company_id)
SELECT company_name FROM company c
JOIN average_price_per_company_CTE p ON c.company_id = p.company_id
WHERE average_price > 2000;

-- 4th Question
WITH emp_dept_CTE AS (SELECT CONCAT(emp_fname, ' ', emp_lname) AS full_name, dept_name FROM employees
	JOIN departments ON dept_code = emp_dept)
SELECT full_name, dept_name FROM emp_dept_CTE;

-- 5th Question
WITH average_budget_CTE AS (SELECT AVG(dept_budget) AS average_budget FROM departments)
SELECT dept_name, dept_budget FROM departments
WHERE dept_budget > (SELECT average_budget FROM average_budget_CTE);

-- 6th Question
WITH number_of_emp_CTE
AS (SELECT dept_name, emp_dept, COUNT(emp_id) AS number_of_emp FROM employees
JOIN departments ON emp_dept = dept_code
GROUP BY emp_dept, dept_name)
SELECT dept_name, number_of_emp FROM number_of_emp_CTE
WHERE number_of_emp > 1;

-- 7th Question
WITH average_item_price_CTE
AS (SELECT AVG(price) AS average_price FROM items),
average_price_per_company_CTE AS (SELECT company_id, AVG(price) AS average_price_per_company FROM items GROUP BY company_id)
SELECT company_name from company c
JOIN average_price_per_company_CTE p ON c.company_id = p.company_id
WHERE average_price_per_company < (SELECT average_price FROM average_item_price_CTE);
```
