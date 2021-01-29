#1
SELECT employees.emp_no, employees.last_name, employees.first_name, employees.sex, salaries.emp_no
FROM salaries
LEFT JOIN employees ON employees.emp_no=salaries.emp_no;
ORDERBY employees.last_name;

#2
SELECT employees.first_name, employees.last_name, employees.hire_date
FROM employees
WHERE "hire_date" >= '1986-01-01' AND "hire_date" < '1987-01-01'
ORDERBY employees.last_name;

#3
SELECT departments.dept_no, departments.dept_name, dept_manager.emp_no, employees.last_name, employees.first_name
From departments
LEFT JOIN dept_manager ON dept_manager.dept_no = departments.dept_no
LEFT JOIN employees ON dept_manager.emp_no = employees.emp_no
ORDER BY departments.dept_no;

#4
SELECT employees.emp_no, employees.last_name, employees.first_name, departments.dept_name
From employees
LEFT JOIN dept_emp ON employees.emp_no = dept_emp.emp_no
LEFT JOIN departments ON departments.dept_no = dept_emp.dept_no
ORDER BY employees.last_name;

#5
SELECT employees.first_name, employees.last_name, employees.sex
from employees
where employees.first_name = 'Hercules'
and employees.last_name LIKE 'B%' 

#6
SELECT employees.first_name, employees.last_name, employees.emp_no, dept_emp.dept_no, departments.dept_name
From employees
INNER JOIN dept_emp ON employees.emp_no = dept_emp.emp_no
INNER JOIN departments ON departments.dept_no = dept_emp.dept_no
WHERE dept_name = 'Sales'

#7
SELECT employees.first_name, employees.last_name, employees.emp_no, dept_emp.dept_no, departments.dept_name
From employees
INNER JOIN dept_emp ON employees.emp_no = dept_emp.emp_no
INNER JOIN departments ON departments.dept_no = dept_emp.dept_no
WHERE dept_name = 'Sales' or dept_name = 'Development'

#8
Select employees.last_name, COUNT(employees.last_name) AS Frequency
FROM employees
Group by employees.last_name
ORDER BY COUNT(employees.last_name) DESC