### 1、查看表中索引
1. 显示索引名称，索引作用的列
```sql
select * from user_ind_columns where table_name='表名';
```
2. 显示索引的具体信息（创建时间、类型、内存大小）
```sql
select * from all_indexes where table_name='表名';
```
### 2、删除序列
```sql
delete sequence 序列名;
```
### 3、查看存储过程编译错误
```sql
select * from SYS.USER_ERRORS where NAME='存储过程名称';
```
### 4、约束条件相关操作
1. 查看表的约束条件
```sql
select * from user_constraints where table_name='表名';
```
2. 删除约束条件
```sql
alter table 表名 drop constraint 约束条件名;
```
3. 失效约束条件
```sql
alter table 表名 disable constraint 约束条件名;
```
4. 生效约束条件
```sql
alter table 表名 enable constraint 约束条件名;
```
