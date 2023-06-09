### 数据库相关

##### 数据库日期函数

```sql
curdate()   curtime()
MONTH(create_date)  
DATE_FORMAT (create_date, '%Y-%m-%d %H:%i:%s') AS create_date
```

##### case when使用

```sql
select case sex when 0 then '女' else '男' end as sex from user
```

##### 已存在的主键继续递增

```sql
-- 查找当前最大的主键值
SELECT MAX (id) FROM table_name;

-- 将自增长序列值更新为下一条记录的主键值
ALTER TABLE table_name AUTO_INCREMENT = max_id + 1;
```

##### Optional判断null

```java
Data data =  Optional.ofNullable(table)
   		 .map(tableItem -> tableItem.getColumn())
   		 .map(col -> col.getData())
   		 .orElseThrow(() -> new RuntimeException("有 null")) 
    	 .orElse(getDefaultValue()) //一定会执行  但是那不到这个方法的返回值
    	 .orElseGet(() -> getDefaultValue()) //拿得到返回值 
```



##### 公网ip

```shell
nslookup myip.opendns.com resolver1.opendns.com
```

