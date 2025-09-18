# SQL Queries

```sql
SELECT name, color, size FROM production.product;
```

```sql
SELECT name, color, size FROM production.product WHERE list_price > 100;
```

```sql
SELECT name, color, size 
FROM production.product 
WHERE list_price < 100 AND color = 'Black';
```

```sql
SELECT name, color, size 
FROM production.product 
WHERE list_price < 100 AND color = 'Black' 
ORDER BY list_price;
```

```sql
SELECT name, size 
FROM production.product 
WHERE color = 'Black' 
ORDER BY list_price DESC 
LIMIT 5;
```

```sql
SELECT name, color 
FROM production.product 
WHERE color IS NOT NULL AND size IS NOT NULL;
```

```sql
SELECT DISTINCT color 
FROM production.product 
WHERE list_price >= 10 AND list_price <= 50;
```

```sql
SELECT name, color 
FROM production.product 
WHERE name ILIKE 'L_N%';
```

```sql
SELECT name, color 
FROM production.product 
WHERE name LIKE 'L_N%';
```

```sql
SELECT name, color 
FROM production.product 
WHERE name SIMILAR TO '(D|L)%' AND LENGTH(name) > 3;
```

```sql
SELECT name 
FROM production.product 
WHERE sell_start_date < '2013-01-01';
```

```sql
SELECT name 
FROM production.product_subcategory;
```

```sql
SELECT name 
FROM production.product_category;
```

```sql
SELECT first_name 
FROM person.person 
WHERE title = 'Mr.';
```

```sql
SELECT first_name 
FROM person.person 
WHERE title IS NULL;
```

```sql
SELECT name 
FROM production.product 
WHERE name LIKE '__s%' OR name LIKE '__r%';
```

```sql
SELECT name 
FROM production.product 
WHERE name SIMILAR TO '__(s|r)%';
```

```sql
SELECT name 
FROM production.product 
WHERE LENGTH(name) = 5;
```

```sql
SELECT name 
FROM production.product 
WHERE sell_start_date < '2011-03-01' 
   OR sell_end_date >= '2012-04-01';
```

```sql
SELECT list_price 
FROM production.product 
WHERE sell_start_date > '2011-03-01' 
ORDER BY list_price DESC 
LIMIT 1;
```

```sql
SELECT MAX(list_price) 
FROM production.product 
WHERE sell_start_date > '2011-03-01';
```

```sql
SELECT color, COUNT(*) 
FROM production.product 
WHERE list_price >= 30 
GROUP BY color;
```

```sql
SELECT color, COUNT(*) 
FROM production.product  
GROUP BY color 
HAVING MIN(list_price) > 100;
```

```sql
SELECT product_subcategory_id, COUNT(*) 
FROM production.product  
GROUP BY product_subcategory_id;
```

```sql
SELECT product_id, COUNT(*) 
FROM sales.sales_order_detail 
GROUP BY product_id;
```

```sql
SELECT product_id, COUNT(*) 
FROM sales.sales_order_detail 
GROUP BY product_id 
HAVING COUNT(*) > 5;
```

```sql
SELECT customer_id, COUNT(*) 
FROM sales.sales_order_header 
GROUP BY customer_id, order_date 
HAVING COUNT(*) > 1;
```

```sql
SELECT product_id 
FROM production.transaction_history_archive 
GROUP BY product_id 
HAVING COUNT(*) > 3;
```

```sql
SELECT product_id 
FROM production.transaction_history_archive 
GROUP BY product_id 
HAVING COUNT(*) = 3 OR COUNT(*) = 5;
```

```sql
SELECT product_subcategory_id 
FROM production.product 
GROUP BY product_subcategory_id 
HAVING COUNT(*) > 10;
```
