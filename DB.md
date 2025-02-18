# get nth salary
## for all db
SELECT name, salary from #Employee_table e1 WHERE n-1 = ( SELECT COUNT( DISTINCT salary FROM #Employee_table e2 WHERE e2.salary < e1.salary ))
## for mysql
SELECT salary from tbl_name ORDER BY salary DESC LIMIT BY n-1, 1
