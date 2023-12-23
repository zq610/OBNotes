# 连接：用于列连接

## 1、内连接：只保留符合条件的数据，用于在多张表中查找数据（交集）

```sql
SELECT  order_id, o.customer_id, first_name
FROM orders o
JOIN customers 
    ON o.customer_id = customers.customer_id 
```

## 隐式连接语法

```sql
SELECT *
FROM orders o, customers c
WHERE o.customer_id  = c.customer_id
```

## 2、外连接：不仅保留符合条件数据，也保留表中其他数据（全集）

```sql
SELECT *
FROM orders o
LEFT JOIN customers c //保留左表的每一项数据，RIGHT JOIN同理
    ON c.customer_id = o.customer_id
ORDER BY c.customer_id
```

## 3、跨数据库连接：添加数据库前缀即可

```sql
SELECT *
FROM order_items oi
JOIN sql_inventory.products p
    ON oi.product_id = p.product_id
```

## 4、自连接：SELF　JOIN

```sql
SELECT * 
FROM employees e
JOIN employees m
    ON e.reports_to = m_employee_id
```

## 5、自外连接

```sql
SELECT * 
FROM employees e
LEFT JOIN employees m
    ON e.reports_to = m_employee_id
```

## 6、多表连接:JOIN ON 的多次使用

```sql
SELECT 
    p.date,
    p.invoice_id,
    p.amount,
    c.name,
    pm.name
FROM payments p
JOIN payment_methods pm
    ON p.payment_method = pm.payment_method_id
JOIN clients c
    ON p.client_id = c.client_id
```

## 7、复合连接条件：多列值唯一标识某项记录（适用于复合主键）

```sql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
    ON oi.order_id = oin.order_Id
    AND oi.product_id = oin.product_id

    USING (oeder_id,product_id)
```

## 8、USING子句:用于不同表中列名相同时使用

```sql
JOIN clients c
    --ON p.client_id = c.client_id
    USING (client_id)
```

## 9、自然连接NATURAL　JOIN：让系统自己连接具有相同列的表（不建议使用，有风险）

```sql
NATURAL JOIN customers c
```

## 10、交叉连接CROSS JOIN

```sql
CROSS JOIN customers c//显示语法
FROM customers c, orders o //隐式语法
```

# UNION：合并多行查询结果

```sql
SELECT 
    customer_id,
    first_name,
    points,
    'Bronze' AS type
FROM customers
WHERE points < 2000
UNION
SELECT 
    customer_id,
    first_name,
    points,
    'Silver' AS type
FROM customers
WHERE points BETWEEN 2000 AND 3000
UNION
SELECT 
    customer_id,
    first_name,
    points,
    'Gold' AS type
FROM customers
WHERE points > 3000
ORDER BY first_name
```
