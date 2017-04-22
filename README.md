# sql_fun
sql

## Oracle

### generate statistics
```
EXEC dbms_stats.gather_schema_stats('SCOTT', cascade=>TRUE);
EXEC dbms_stats.gather_table_stats('SCOTT','EMP',cascade=>TRUE);
```


## Recursive SQL

#### select numbers from 0 to 1000
```
with recursive blah(n) as (
	select 0 n 
	union all
	select n + 1 from blah where n<1000
)
select n from blah;
```

#### create table with dates between 19000101 and 21000101
```
create table dates as with recursive mydates(tdate) as (
	select cast ('19000101' as date) tdate
	union all
	select cast (tdate + interval '1 day' as date) tdate
	from mydates 
	where tdate <= '21000101'
)
select * from mydates;
```



