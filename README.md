# Mat301-ps1
Homework 
### Problem Set 1 - Introduction to DQL 
---

Before we begin, it is noteworthy to list the synonyms for various database terminology.  

|Row |Column   | 
|:--- |:---- |
|Records  | Field |
| Recordset | Attribute |
|Tuple | Component  |

---

Data Query Language (DQL) is a sub-language of Structured Query Language (SQL).  

#### SELECT statement

The `SELECT` statement is the one (and only) statement needed to construct database queries.  A query extracts data from the database.  A `SELECT` statement **must** contain a `FROM` clause.  The basic syntax for `SELECT` statement is:

```SQL
SELECT column(s) FROM table(s)
```

Often (although not necessary) each statement/clause is written at the beginning of a line.  In particular, 

```SQL
SELECT column(s) 
FROM table(s)
```

NOTE: If database is housed on a shared server, the database name must proceed the table name separated with the dot notation.  In particular, 

```SQL
SELECT column(s) 
FROM database.table
```

If multiple columns are desired in the query results, a comma delimited list of column names is supplied after the `SELECT` statement. Similar a list of one or more tables follows the FROM clause.   The query below SELECTs `column1`, `column2`, and `column3`. 


```SQL
SELECT column1, column2, column3 FROM database.table;
```



The * is a wildcard and returns **all** columns from the table.  

For example, the following query will return the entire table (use with caution).

```SQL
SELECT * FROM database.table;
```


#### The WHERE clause

The `WHERE` clause is a conditional that limits the number of records returned to ones that match a specified *condition*.  The value of the condition is TRUE or FALSE.  The `WHERE` clause limits or **filters** the number of records returned by the query. The general syntax is:

```SQL
SELECT column(s)
FROM database.table
WHERE [condition]
```
For example, selecting all records from the products table where country is China, 

```SQL
SELECT *
FROM Products
WHERE country='China';
```


Multiple/complex conditions can be specified using `AND` or `OR`.  In particular,

```SQL
SELECT column(s)
FROM database.table
WHERE [condition1] AND/OR [condition2]
```


#### The ORDER BY clause

Another clause that can be added to a `SELECT` statment is the `ORDER BY` clause.  Like the name implies, it will order the records in ascending or descending order.  Ascending is default.  It can be used with or without the `WHERE` clause.  

```SQL
SELECT column1, column2
FROM database.table
ORDER BY column2;
```

#### The DISTINCT option

The `DISTINCT` option is used in a query to select distinct records.  The syntax is, 

```SQL
SELECT DISTINCT column
FROM database.table;
```



#### The COUNT function

The `COUNT` function is used, as the name implies, to count the results of the query.    

```SQL
SELECT COUNT(*)
FROM database.table;
```

---

#### Exercises

**Directions**: Create a GitHub account.  All assignments will be submitted to your GitHub account.  You can use any format (e.g., .md, .txt) EXCEPT word processors (e.g., MS Word) to upload your solutions.  All queries will use the `Products` table.  Connect to the database.  Copy [Products.sql](https://github.com/jamesquinlan/mat301/tree/master/products), change database name to your database, paste in Query window, then execute.

===

1. What does SQL stand for?  How is it pronounced? 

 Structured Query Language. Pronounced "Es Que El" or "Sequel" 

2. Are SQL commands case-sensitive?  How can you determine? 

 No they are not case sensitive. They are case insensitive. 

3. What does DQL stand for?

 Data query language 

4. True or False:  Is it necessary to use the `FROM` clause with the select statement? 

 Yes it is necessary 

5. True or False:  Is it necessary to use a `WHERE` clause?  If not, when and why would you use a `WHERE` clause?

 False: You would use it when you want to, for example, select a price from products where price is > 9.99. In this instance we need the 'where' clause to specify the price being slected. 

6. What is the purpose of the `ORDER BY` clause?  What is its default value?  

 Default value is ascending. The 'ORDER BY' clause allows you to select products from a table and sort them, by price for example. 

7. Is the data in the products table case sensitive?  Should it be case sensitive/insensitive? 
 
 It is case sensitive for product and column names. However, the keywords are NOT case sensitive (select, from, etc.) It is the objects that are case sensitive. 

8. Select all product names.

 Select name from unemath_Cote.Products;

9. List the MSRP for all products in ascending order.

 Select msrp from unemath_Cote.Products order by msrp;

10. Find all products within  category 430.  What is category 430?

 Select product_id from unemath_Cote.Products where category_id=430; 

 Category 430 is glasses.

11. Find all product id and names in category 430 manufactured by 428.

 Select product_id from unemath_Cote.Products where category_id=430 and manufacturer_id=428;

12. How many products in category 430 manufactured by 428?
 
 Select count from unemath_Cote.Products where category_id=430 and manufacturer_id=428;

 18.

13. How many countries make products contained in the store?

 SELECT country, count(*) FROM unemath_Cote.Products group by country; 

14. How many products are manufactured in the USA?

 Select count(*) from unemath_Cote.Products where country='usa';

 4091

15. How many products cost the company less than $10?

 Select count(*) from unemath_Cote.Products where msrp <10;

 3482

16. How many products cost the company less than $10 and sell for more than $20?

 Select count(*) from unemath_Cote.Products where msrp >20 and price <10;

 40.

17. How many products cost the company less than $10 and sell for less than $20?

 Select count(*) from unemath_Cote.Products where msrp <20 and price <10;

 7523

18. Which products cost less than $10 and sell for more than $20?

 Select name from unemath_Cote.Products where msrp >20 and price <10;

19. Count all product's that have shipping weight less than 1 pound or greater than 20 pounds.

 SELECT count(*) from unemath_Cote.Products where ship_weight <1 or ship_weight >20;

20. Create your own query.

How many products cost $10 and $11? 

Select count(*) from unemath_Cote.Products where msrp=10 and 11;

