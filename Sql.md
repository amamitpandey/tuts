### SQL query

## Questions
### primary key :
should be not null and unique
### foriegn key :
make a relationship between two table, ex, department_id from employee_tbl and department_tbl
### unique key :
can be one time null and unique row wise
### Join:
- ineer join/ join: common data between two table, subset of left and right table
- left join : inner join + left join  (full table data of left tbl)
- right join : inner join + right join (full table data of right tbl)
- full join : left + right join
- union : left + right join - duplicates
- cross join : target cross element like 2*2 array

  ```
  // ineer join
SELECT * FROM 
employee_tbl e
JOIN department_tble d
ON e.employee_id==d.employee_id;
  
  ```

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

### use cases 
```
SELECT
  column1,
  column2,
  CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE result_default
  END AS alias_name
FROM your_table;

```

### use case with join with two diffrent table
```
SELECT 
  c.name,
  o.amount,
  CASE 
    WHEN o.amount >= 1000 THEN 'High Spender'
    WHEN o.amount >= 500 THEN 'Medium Spender'
    ELSE 'Low Spender'
  END AS spender_level
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;
``` 
### How to test delete sql query, it don't return anything
1. to test it, we can see affected row by sqlquery.excuteUpdate(), assertequal(1,affectedRow).
2. first delete by user than try to find it again if notfound means deleted.

### Composite key: pair of tow parimary key form two table, like student_id+course_id, purpose is make a unique key in colume
in java, we can use @mbeddable and @EmbeddedId
```
@Embeddable
public class OrderId implements Serializable {
    private Long userId;
    private Long productId;

    // equals, hashCode, getters, setters
}

@Entity
public class Order {
    @EmbeddedId
    private OrderId id;

    private int quantity;
    // ...
}

```
in sql, we can use
```
CREATE TABLE orders (
    user_id INT,
    product_id INT,
    order_date DATE,
    quantity INT,
    PRIMARY KEY (user_id, product_id)
);

```






