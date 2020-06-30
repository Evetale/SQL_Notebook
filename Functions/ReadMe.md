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

**2. Wildcards used in LIKE**  
There are 4 types of wildcards in total:

Wildcard character | Description
--------------- | ------------------
%  | Any string of zero or more characters
_  | Any Single character
[] | Any Single character within the range
[^] | Any Single character not within the range

In addtion, keyword *ESCAPE* can be used to help escape character in the wildcard parttern.  
Example:
```
Select *
FROM (VALUES('store_1', 'first week 20% off')
			,('store_2', 'second one $20 off')
			, ('store_3', 'buy 2 get 1 80% off')
	  ) AS a(store_name, discount)
--% will not be escaped in below parttern
WHERE discount LIKE '%20%%'
```
Above code will return

store_name | discount
----------- | ----------
store_1 | first week 20% off
store_2 | second one $20 off

If change the where clause to
```
-- $ is used as escape character in below
WHERE discount LIKE '%20$%%' ESCAPE '$'
```
The result will be

store_name | discount
----------- | ----------
store_1 | first week 20% off

**3. Cube / Grouping Set /Rollup**
