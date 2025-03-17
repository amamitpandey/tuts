### SQL query

## Questions
### SQL Query to Count the Number of Employees in Each Department sql
```
SELECT department_name, COUNT(*) AS employee_count
FROM employees
GROUP BY department_name;
```
### get second highest salary of employee
```
SELECT salary
FROM employees
GROUP BY salary
ORDER BY salary DESC
LIMIT 1 OFFSET 1;
```

