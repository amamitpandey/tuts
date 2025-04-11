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
### DataBase model:
it's relationship between entity(table structure) and DB table, in general purpose called native SQL query.
```
SELECT * FROM ...

```

### View: it's a virtual table to simplify complex query and sharing peupose.
In schema view save complex custom query that we can share as per user role to just excute the query.
this view can update and drop.

```
CREATE VIEW student_enrollments AS
SELECT 
    s.student_id,
    CONCAT(s.first_name, ' ', s.last_name) AS student_name,
    c.course_name,
    e.enrollment_date
FROM 
    Student s
JOIN 
    Enrollment e ON s.student_id = e.student_id
JOIN 
    Course c ON c.course_id = e.course_id;

```
### How to test delete sql query, it don't return anything
1. to test it, we can see affected row by sqlquery.excuteUpdate(), assertequal(1,affectedRow).
2. first delete by user than try to find it again if notfound means deleted.   



