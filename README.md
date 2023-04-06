## sportvserve_assignment
Take Away Home Assignment for Big Data Engineer

EmployeeInfo Table
EmpID| EmpFname |EmpLname |Department| Project |Address        | DOB        |Gender
-----|----------|---------|----------|---------|---------------|------------|-------
1    | Sanjay   |   Mehra | HR       |P1       | Hyderabad(HYD)| 01/12/1976 |M                                                                   
2    |  Ananya  | Mishra  |Admin     |P2       |Delhi(DEL)     |02/05/1968  |F                                                                 
3    |Rohan.    | Diwan   |Account   |P3.      | Mumbai(BOM)   |01/01/1980  |M                                                                 
4    |Sonia.    | Kulkarni| HR       |P1       |Hyderabad(HYD) |02/05/1992  |F                                                               
5    |Ankit     |Kapoor   |Admin     |P2       |Delhi(DEL)     |03/07/1994  | M

EmployeePosition Table:
EmpID |EmpPosition |DateOfJoining |Salary
------|------------|--------------|-------------------
1     |Manager     |01/05/2022    |  500000
2     |Executive   |02/05/2022    | 75000
3     |Manager     |01/05/2022    | 90000
2     |Lead        |02/05/2022    |  85000
1     |Executive   |01/05/2022    | 300000

1. Write a query to fetch the number of employees working in the department ‘HR’.
```
SELECT COUNT(*) FROM EmployeeInfo WHERE Department = 'HR';
```
2. Write a query to create a new table which consists of data and structure copied from the other table.
```
CREATE TABLE NewTable LIKE EmployeePosition;
```
3. Write a query to retrieve the EmpFname and EmpLname in a single column as “FullName”. The first name
and the last name must be separated with space.
```
SELECT CONCAT(EmpFname, ' ', EmpLname) AS FullName FROM EmployeeInfo;
```
4. Write a query to fetch all employees who also hold the managerial position.
```
SELECT * FROM EmployeePosition WHERE EmpPosition = 'Manager';
```
5. Write a query to fetch the department-wise count of employees sorted by department’s count in ascending
order.
```
SELECT EmpPosition, COUNT(*) AS EmployeeCount FROM EmployeePosition GROUP BY EmpPosition ORDER BY EmployeeCount ASC;
```
6. Write a recursive CTE that will display in order all the dates of a given month (e.g. Jan 1, Jan
2,...Jan 31) 
```
WITH RECURSIVE dates(date) AS (
  SELECT CAST('2022-01-01' AS DATE)
  UNION ALL
  SELECT date + INTERVAL 1 DAY
  FROM dates
  WHERE date < '2022-01-31'
)
SELECT date_format(date, '%b %e') AS Date
FROM dates;
```
