###**[176. Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)**

```sql
Create table If Not Exists Employee (Id int, Salary int)
Truncate table Employee
insert into Employee (Id, Salary) values ('1', '100')
insert into Employee (Id, Salary) values ('2', '200')
insert into Employee (Id, Salary) values ('3', '300')
```
Write a SQL query to get the second highest salary from the Employee table.

| Id | Salary |
|----|--------|
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |

For example, given the above Employee table, the query should return 200 as the second highest salary. If there is no second highest salary, then the query should return null.

| SecondHighestSalary |
|---------------------|
| 200                 |

```sql
Solution#1
select Max(Salary) as 'SecondHighestSalary' from Employee where Salary not in (select Max(Salary) from Employee);

Solution#2
select Max(Salary) as 'SecondHighestSalary' from Employee where Salary < (select Max(Salary) from Employee);

Solution#3
#select Salary as SecondHighestSalary from (select Salary FROM Employee ORDER BY salary DESC LIMIT 2) as emp ORDER BY salary asc limit 1; 
```
