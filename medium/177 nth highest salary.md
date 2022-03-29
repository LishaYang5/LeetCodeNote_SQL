# Problem name: 177 Nth highest salary
Link: 

```
CREAT FUNCTION getNthHighestSalary(@N INT) RETURNS INT AS
BEGIN 
    RETURN(
        SELECT DISTINCT salary
            FROM(
                SELECT salary
                ,dense_rank() over (order by salary desc) as dr
                from Employee
            ) AS source
            where dr=@N
    );
END
```