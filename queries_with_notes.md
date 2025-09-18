# SQL-запросы к базе данных

## 1. Все товары (имя, цвет, размер)
```sql
SELECT name, color, size FROM production.product;
```

## 2. Товары дороже 100
```sql
SELECT name, color, size FROM production.product WHERE list_price > 100;
```

## 3. Товары дешевле 100 и черного цвета
```sql
SELECT name, color, size 
FROM production.product 
WHERE list_price < 100 AND color = 'Black';
```

## 4. То же самое, но с сортировкой по цене
```sql
SELECT name, color, size 
FROM production.product 
WHERE list_price < 100 AND color = 'Black' 
ORDER BY list_price;
```

## 5. 5 самых дорогих черных товаров
```sql
SELECT name, size 
FROM production.product 
WHERE color = 'Black' 
ORDER BY list_price DESC 
LIMIT 5;
```

## 6. Товары с непустыми цветом и размером
```sql
SELECT name, color 
FROM production.product 
WHERE color IS NOT NULL AND size IS NOT NULL;
```

## 7. Уникальные цвета товаров с ценой от 10 до 50
```sql
SELECT DISTINCT color 
FROM production.product 
WHERE list_price >= 10 AND list_price <= 50;
```

## 8. Товары, начинающиеся на "L_N"
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

## 9. Названия на D или L, длина > 3
```sql
SELECT name, color 
FROM production.product 
WHERE name SIMILAR TO '(D|L)%' AND LENGTH(name) > 3;
```

## 10. Товары с началом продаж до 2013-01-01
```sql
SELECT name 
FROM production.product 
WHERE sell_start_date < '2013-01-01';
```

## 11. Подкатегории товаров
```sql
SELECT name 
FROM production.product_subcategory;
```

## 12. Категории товаров
```sql
SELECT name 
FROM production.product_category;
```

## 13. Люди с титулом "Mr."
```sql
SELECT first_name 
FROM person.person 
WHERE title = 'Mr.';
```

## 14. Люди без титула
```sql
SELECT first_name 
FROM person.person 
WHERE title IS NULL;
```

## 15. Товары, начинающиеся на __s или __r
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

## 16. Названия длиной 5 символов
```sql
SELECT name 
FROM production.product 
WHERE LENGTH(name) = 5;
```

## 17. Фильтр по датам начала/окончания продаж
```sql
SELECT name 
FROM production.product 
WHERE sell_start_date < '2011-03-01' 
   OR sell_end_date >= '2012-04-01';
```

## 18. Максимальная цена товара после 2011-03-01
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

## 19. Количество товаров по цвету (цена >= 30)
```sql
SELECT color, COUNT(*) 
FROM production.product 
WHERE list_price >= 30 
GROUP BY color;
```

## 20. Цвета, где минимальная цена > 100
```sql
SELECT color, COUNT(*) 
FROM production.product  
GROUP BY color 
HAVING MIN(list_price) > 100;
```

## 21. Количество товаров по подкатегориям
```sql
SELECT product_subcategory_id, COUNT(*) 
FROM production.product  
GROUP BY product_subcategory_id;
```

## 22. Количество заказов по каждому товару
```sql
SELECT product_id, COUNT(*) 
FROM sales.sales_order_detail 
GROUP BY product_id;
```

## 23. Товары, заказанные более 5 раз
```sql
SELECT product_id, COUNT(*) 
FROM sales.sales_order_detail 
GROUP BY product_id 
HAVING COUNT(*) > 5;
```

## 24. Клиенты с несколькими заказами в один день
```sql
SELECT customer_id, COUNT(*) 
FROM sales.sales_order_header 
GROUP BY customer_id, order_date 
HAVING COUNT(*) > 1;
```

## 26. Товары с количеством транзакций > 3
```sql
SELECT product_id 
FROM production.transaction_history_archive 
GROUP BY product_id 
HAVING COUNT(*) > 3;
```

## 27. Товары с количеством транзакций = 3 или = 5
```sql
SELECT product_id 
FROM production.transaction_history_archive 
GROUP BY product_id 
HAVING COUNT(*) = 3 OR COUNT(*) = 5;
```

## 28. Подкатегории, где товаров больше 10
```sql
SELECT product_subcategory_id 
FROM production.product 
GROUP BY product_subcategory_id 
HAVING COUNT(*) > 10;
```