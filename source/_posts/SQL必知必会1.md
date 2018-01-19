---
title: SQL必知必会1
date: 2017-10-22 22:54:44
tags: 
- Oracle PL/SQL 必知必会
- 书
---
*前言：但行好事，莫问前程*
**检索数据**
````sql
SELECT products.prod_name --products为表名
FROM crashcourse.products;--crashcourse为数据库名
````
**对检索的数据进行排序**
````sql
SELECT prod_name
FROM products
ORDER BY prod_name;--按字母升序排列
````
````sql
SELECT prod_id,prod_price,prod_name
FROM products
ORDER BY prod_price,prod_name;--注意有优先级,先按prod_price排序
````
````sql
SELECT prod_id,prod_price,prod_name
FROM products
ORDER BY prod_price DESC,prod_name;--prod_price降序,prod_name升序
````
**过滤数据**
````sql
SELECT prod_name
FROM products
WHERE pro_price IS NULL; --空字段
````
**高级过滤数据**
````sql
SELECT prod_name,prod_price
FROM products
WHERE (vend_id=1002 OR vend_id=1003) AND prod_price>=10;--注意AND优先级更高
````
````sql
SELECT prod_name,prod_price
FROM products
WHERE vend_id NOT IN (1002,1003)
ORDER BY prod_name;
````
**使用通配符过滤**
````sql
SELECT prod_id,prod_name
FROM products
WHERE prod_name LIKE '_Jet%';--区分大小写,‘%’代表[0,正无穷)个字符,‘_’匹配单个字符
````

**使用正则表达式执行搜索**
````sql
SELECT prod_name;
FROM products
WHERE REGEXP_LIKE(prod_name,'^\(\d{4,5} sticks?\)$');--注意转义字符的使用
--\d=[0-9]  \D=[^0-9] \w=[a-zA-Z0-9]   \s=任意空白字符  \S=任意非空白字符  ^=开头(^有两种意思:取反和开头) $=末尾
````
