#### 自定义排序

```sql
order by fifld(field_name,'','')
```

#### 空值排序

```sql
order by if(ifnull(filed_name),0,1)
```

#### case....when表达式

```sql
case when.. then ..  else ..  end filed_name
```

#### 分组连接函数 (GROUP_CONCAT)

```SQL
select group_concat(filed_name order by price desc separator ',')
```

#### 分组统计后再进行统计汇总(WITH ROLLUP)

```sql
with rollup
```

#### 子查询提取 with as

```sql
with m1 as (select * from movies where price > 50),
m2 as (select * from mmovies where price < 50)
select * from m1 where m1.id not in (select m2.id from m2) and m1.id = 1;
```

#### 覆盖插入(replace into)   有删除+插入