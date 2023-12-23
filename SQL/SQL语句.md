# 一、查询

## 1、总体用法

```sql
SELECT *
FROM customers
WHERE customer_id = 1
ORDER BY firstname
//注释
-- WHERE customer_id = 1
```

## 2、选择语句SELECT

```sql
\\1、选择表的所有列
SELECT *
FROM customers
\\2、选择特定列，并做运算
SELECT 
    last_name,
    first_name, 
    points,
    --(points+10) * 100 AS discount_factor
    (points+10) * 100 AS 'discount factor'
FROM customers
\\3、选择列去重（当目标列存在重复时）
SELECT DISTINCT state
FROM customers
```

## 3、WHERE语句

```sql
SELECT *
FROM orders
WHERE birth_date >= '1990-01-01'
```

**运算符**

- > 

- <

- <>和!=

- AND(优先)

- OR

- NOT

- IN：用于表示符合条件，简略语句
  
  ```sql
  SELECT *
  FROM customers
  --WHERE state = 'VA' OR state = 'FL' OR state = 'GA'
  WHERE state IN ('VA','FL','GA')
  ```

- BETWEEN ... AND...

- LIKE
  
  ```sql
  SELECT *
  FROM customers
  WHERE last_name LIKE 'B%'
  //模糊查找：不区分大小写
  //_表示单字符
  //%表示任意个字符
  WHERE address LIKE '%trail%' OR
        address LIKE '%avenue%'
  WHERE PhoneNumber LIKE '%9'
  ```

- REGEXP （正则表达式）**^、$、|、[]**
  
  ```sql
  SELECT *
  FROM customers
  WHERE lastname REGEXP 'filed'
  WHERE lastname REGEXP '^filed'//开头
  WHERE lastname REGEXP 'filed$'//末尾
  WHERE lastname REGEXP 'filed|mac|rose'
  WHERE lastname REGEXP '[abced]i'//ai|bi|...
  WHERE lastname REGEXP '[a-d]i'
  ```

- NULL
  
  ```sql
  WHERE phone IS NOT NUL 
  ```

## 4、ORDER BY语句

```sql
SELECT *
FROM customers
ORDER BY state , birth_date DESC
//DESC表示降序
```

## 5、LIMIT语句

```sql
SELECT *
FROM customers
LIMIT 10// 前10项
LIMIT 6，3//获取6项后的3项 其中6为偏移量 
```
