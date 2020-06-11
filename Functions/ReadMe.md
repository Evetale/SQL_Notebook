## SQL Functions
### MS SQL Sever
*All examples are based on database AdventureWorks2017*  
**1. OFFSET + FETCH**  
These can only be used after ORDER BY CLAUSE. The syntax is as below:  
```
ORDER BY order_by_expression [ASC | DESC]
OFFSET {integer_num | count_expression} ROWS
FETCH NEXT {integer_num | count_expression} ROWS ONLY
```
Example:
```
Select *
FROM Person.Address
ORDER BY AddressID OFFSET 10 ROWS FETCH NEXT 5 ROWS ONLY
```
**2. Cube / Grouping Set /Rollup**
